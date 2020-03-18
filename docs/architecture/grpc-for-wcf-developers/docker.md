---
title: Docker - gRPC dla programistów WCF
description: Tworzenie obrazów platformy Docker dla aplikacji ASP.NET Core gRPC
ms.date: 09/02/2019
ms.openlocfilehash: e67c43f9486fbfe9a5d3e84e3b74770eb621f604
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148117"
---
# <a name="create-docker-images"></a>Tworzenie obrazów platformy Docker

Ta sekcja obejmuje tworzenie obrazów platformy Docker dla ASP.NET podstawowych aplikacji gRPC, gotowych do pracy w platformie Docker, Kubernetes lub innych środowiskach kontenerów. Przykładowa aplikacja używana z ASP.NET podstawową aplikacją sieci web MVC i usługą gRPC jest dostępna w repozytorium [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w serwisie GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core

Firma Microsoft udostępnia szereg obrazów podstawowych do tworzenia i uruchamiania aplikacji .NET Core. Aby utworzyć ASP.NET obraz core 3.0, należy użyć dwóch obrazów podstawowych:

- Obraz sdk do tworzenia i publikowania aplikacji.
- Obraz w czasie wykonywania dla wdrożenia.

| Image (Obraz) | Opis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Do tworzenia `docker build`aplikacji z . Nie do wykorzystania w produkcji. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Zawiera zależności runtime i ASP.NET Core. Do produkcji. |

Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach Linuksa, wyróżniające się tagami.

| Znaczniki obrazu | Linux | Uwagi |
| --------- | ----- | ----- |
| 3.0-buster, 3.0 | Debian 10 | Domyślny obraz, jeśli nie określono wariantu os. |
| 3.0-alpejski | Alpejski 3,9 | Alpejskie obrazy bazowe są znacznie mniejsze niż obrazy Debiana lub Ubuntu. |
| 3.0-dyskoteka | Ubuntu 19.04 | |
| 3.0-bionic | Ubuntu 18.04 | |

Alpejski obraz bazowy wynosi około 100 MB, w porównaniu do 200 MB dla obrazów Debiana i Ubuntu. Niektóre pakiety oprogramowania lub biblioteki mogą nie być dostępne w zarządzaniu pakietami firmy Alpine. Jeśli nie masz pewności, którego obrazu użyć, prawdopodobnie powinieneś wybrać domyślnego Debiana.

> [!IMPORTANT]
> Upewnij się, że używasz tego samego wariantu systemu Linux dla kompilacji i w czasie wykonywania. Aplikacje utworzone i opublikowane w jednym wariancie mogą nie działać na innym.

## <a name="create-a-docker-image"></a>Tworzenie obrazu platformy Docker

Obraz platformy Docker jest definiowany przez *plik Dockerfile*. Jest to plik tekstowy, który zawiera wszystkie polecenia potrzebne do tworzenia aplikacji i instalowania wszelkich zależności, które są wymagane do tworzenia lub uruchamiania aplikacji. W poniższym przykładzie przedstawiono najprostszy plik Dockerfile dla ASP.NET aplikacji Core 3.0:

```dockerfile
# Application build steps
FROM mcr.microsoft.com/dotnet/core/sdk:3.0 as builder

WORKDIR /src

COPY . .

RUN dotnet restore

RUN dotnet publish -c Release -o /published src/StockData/StockData.csproj

# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

# Uncomment the line below if running with HTTPS
# ENV ASPNETCORE_URLS=https://+:443

WORKDIR /app

COPY --from=builder /published .

ENTRYPOINT [ "dotnet", "StockData.dll" ]
```

Plik Dockerfile składa się z `sdk` dwóch części: pierwszy używa obrazu podstawowego do tworzenia i publikowania aplikacji; drugi tworzy obraz czasu wykonywania `aspnet` z podstawy. Jest tak, `sdk` ponieważ obraz jest około 900 MB, w porównaniu do około 200 MB dla obrazu w czasie wykonywania, a większość jego zawartości są niepotrzebne w czasie wykonywania.

### <a name="the-build-steps"></a>Kroki kompilacji

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje obraz podstawowy i przypisuje `builder` alias. |
| `WORKDIR /src` | Tworzy `/src` katalog i ustawia go jako bieżący katalog roboczy. |
| `COPY . .` | Kopiuje wszystko poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie. |
| `RUN dotnet restore` | Przywraca wszystkie pakiety zewnętrzne (ASP.NET framework Core 3.0 jest preinstalowany z zestawem SDK). |
| `RUN dotnet publish ...` | Tworzy i publikuje kompilację wydania. Należy pamiętać, że flaga `--runtime` nie jest wymagana. |

### <a name="the-runtime-image-steps"></a>Kroki obrazu w czasie wykonywania

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje nowy obraz podstawowy. |
| `WORKDIR /app` | Tworzy `/app` katalog i ustawia go jako bieżący katalog roboczy. |
| `COPY --from=builder ...` | Kopiuje opublikowaną aplikację z poprzedniego `builder` obrazu, używając `FROM` aliasu z pierwszego wiersza. |
| `ENTRYPOINT [ ... ]` | Ustawia polecenie do uruchomienia po uruchomieniu kontenera. Polecenie `dotnet` w obrazie w czasie wykonywania można uruchamiać tylko pliki DLL. |

### <a name="https-in-docker"></a>HTTPS w platformie Docker

Obrazy podstawowe firmy Microsoft `ASPNETCORE_URLS` dla platformy Docker ustawiono zmienną środowiskową na `http://+:80`, co oznacza, że Kestrel działa bez protokołu HTTPS na tym porcie. Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w [aplikacjach gRPC hostowanych](self-hosted.md)samodzielnie ), należy to zastąpić. Ustaw zmienną środowiskową w części tworzenia obrazu środowiska uruchomieniowego pliku Dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Plik .dockerignore

Podobnie `.gitignore` jak pliki, które wykluczają niektóre pliki `.dockerignore` i katalogi z kontroli źródła, plik może służyć do wykluczenia plików i katalogów z kopiowania do obrazu podczas kompilacji. Pozwala to nie tylko zaoszczędzić czas kopiowania, ale także `obj` uniknąć pewnych błędów wynikających z kopiowania katalogu z komputera do obrazu. Co najmniej należy dodać wpisy `bin` dla `obj` i `.dockerignore` do pliku.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Tworzenie obrazu

Dla rozwiązania z jednej aplikacji, a tym samym jeden plik Dockerfile, jest najprostszym umieścić Plik Dockerfile w katalogu podstawowym. Innymi słowy, umieść go w tym `.sln` samym katalogu co plik. W takim przypadku, aby utworzyć obraz, użyj następującego `docker build` polecenia z katalogu zawierającego Plik Dockerfile.

```console
docker build --tag stockdata .
```

Myląco `--tag` nazwana flaga (która może zostać skrócona do `-t`) określa całą nazwę obrazu, w tym rzeczywisty tag, jeśli został określony. Na `.` końcu określa kontekst, w którym kompilacja zostanie uruchomiony; bieżącego katalogu roboczego `COPY` dla poleceń w pliku Dockerfile.

Jeśli masz wiele aplikacji w ramach jednego rozwiązania, można zachować Dockerfile dla `.csproj` każdej aplikacji w swoim folderze, obok pliku. Nadal należy uruchomić `docker build` polecenie z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu. Plik dockerfile można określić poniżej bieżącego `--file` katalogu, używając flagi (lub `-f`) .

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Uruchamianie obrazu w kontenerze na komputerze

Aby uruchomić obraz w lokalnym wystąpieniu `docker run` platformy Docker, użyj tego polecenia.

```console
docker run -ti -p 5000:80 stockdata
```

Flaga `-ti` łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym. Publikuje `-p 5000:80` (łączy) port 80 w kontenerze do portu 5000 w interfejsie sieci localhost.

## <a name="push-the-image-to-a-registry"></a>Wypychanie obrazu do rejestru

Po sprawdzoniu, że obraz działa, wypchnij go do rejestru platformy Docker, aby udostępnić go w innych systemach. Sieci wewnętrzne będą musiały aprowizować rejestr platformy Docker. Może to być tak proste, jak uruchamianie [własnego `registry` obrazu platformy Docker](https://docs.docker.com/registry/deploying/) (rejestr platformy Docker jest uruchamiany w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania. Do udostępniania zewnętrznego i korzystania z chmury dostępne są różne zarządzane rejestry, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Aby wypchnąć do centrum docker, prefiks nazwy obrazu z nazwą użytkownika lub organizacji.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Aby wypchnąć do rejestru prywatnego, prefiks nazwy obrazu z nazwą hosta rejestru i nazwą organizacji.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Po obraz znajduje się w rejestrze, można wdrożyć go do poszczególnych hostów platformy Docker lub do aparatu aranżacji kontenerów, takich jak Kubernetes.

>[!div class="step-by-step"]
>[Poprzedni](self-hosted.md)
>[następny](kubernetes.md)
