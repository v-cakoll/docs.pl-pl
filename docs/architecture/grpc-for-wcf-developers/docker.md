---
title: Docker-gRPC dla deweloperów WCF
description: Tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 6e9d4956077286d133d09ab8e681ba5e82ab1aa4
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184478"
---
# <a name="docker"></a>Docker

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Ta sekcja będzie obejmować tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC, gotowych do uruchamiania w środowiskach Docker, Kubernetes i innych kontenerach. Przykładowa aplikacja używana z aplikacją sieci Web ASP.NET Core MVC i usługą gRPC jest dostępna w repozytorium [RendleLabs/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core

Firma Microsoft udostępnia wiele podstawowych obrazów do kompilowania i uruchamiania aplikacji platformy .NET Core. Do utworzenia obrazu ASP.NET Core 3,0 są używane dwa obrazy podstawowe: obraz zestawu SDK do kompilowania i publikowania aplikacji oraz obraz środowiska uruchomieniowego na potrzeby wdrożenia.

| Obraz | Opis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Do kompilowania aplikacji `docker build`za pomocą programu. Nie do użycia w środowisku produkcyjnym. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Zawiera zależności środowiska uruchomieniowego i ASP.NET Core. Dla środowiska produkcyjnego. |

Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach systemu Linux, które różnią się od tagów.

| Tagi obrazu | Linux | Uwagi |
| --------- | ----- | ----- |
| 3,0 – Buster, 3,0 | Debian 10 | Obraz domyślny, jeśli nie określono żadnego wariantu systemu operacyjnego. |
| 3,0 — Alpine | Alpine 3,9 | Obrazy Alpine Base są znacznie mniejsze niż Debian lub Ubuntu. |
| 3,0 – Disco | Ubuntu 19,04 | |
| 3,0 – Bionic | Ubuntu 18.04 | |

Obraz Alpine Base ma około 100 MB, w porównaniu do 200 MB dla obrazów Debian i Ubuntu, ale niektóre pakiety oprogramowania lub biblioteki mogą nie być dostępne w usłudze Alpine Package Management. Jeśli nie masz pewności, którego obrazu użyć, najlepiej naDebian się na domyślne, chyba że masz atrakcyjną potrzebę używania innego dystrybucjiu.

> [!IMPORTANT]
> Upewnij się, że używasz tego samego wariantu systemu Linux do kompilowania i środowiska uruchomieniowego. Aplikacje skompilowane i opublikowane na jednym z wariantów mogą nie zadziałały na innym.

## <a name="create-a-docker-image"></a>Tworzenie obrazu platformy Docker

Obraz platformy Docker jest definiowany przez *pliku dockerfile*, plik tekstowy, który zawiera wszystkie polecenia, które są potrzebne do skompilowania aplikacji i zainstalowania wszelkich zależności, które są wymagane do tworzenia lub uruchamiania aplikacji. Poniższy przykład pokazuje najprostszą pliku dockerfile dla aplikacji ASP.NET Core 3,0:

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

Pliku dockerfile ma dwie części: pierwszy z nich używa `sdk` obrazu podstawowego do kompilowania i publikowania aplikacji. drugi tworzy obraz środowiska uruchomieniowego `aspnet` z bazy. Jest to spowodowane `sdk` tym, że obraz jest około 900 MB w porównaniu do około 200 MB dla obrazu środowiska uruchomieniowego. większość jego zawartości jest niezbędna w czasie wykonywania.

### <a name="the-build-steps"></a>Kroki kompilacji

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje podstawowy obraz i przypisuje `builder` alias (zobacz następną sekcję dla wyjaśnienia). |
| `WORKDIR /src` | `/src` Tworzy katalog i ustawia go jako bieżący katalog roboczy. |
| `COPY . .` | Kopiuje wszystkie elementy znajdujące się poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie. |
| `RUN dotnet restore` | Przywraca wszystkie pakiety zewnętrzne (ASP.NET Core 3,0 Framework jest wstępnie zainstalowany wraz z zestawem SDK). |
| `RUN dotnet publish ...` | Kompiluje i publikuje kompilację wydania. Należy zauważyć, `--runtime` że flaga nie jest wymagana. |

### <a name="the-runtime-image-steps"></a>Kroki obrazu środowiska uruchomieniowego

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje nowy obraz podstawowy. |
| `WORKDIR /app` | `/app` Tworzy katalog i ustawia go jako bieżący katalog roboczy. |
| `COPY --from=builder ...` | Kopiuje opublikowaną aplikację z poprzedniego obrazu przy użyciu `builder` aliasu z pierwszego `FROM` wiersza. |
| `ENTRYPOINT [ ... ]` | Ustawia polecenie, które ma być uruchamiane po rozpoczęciu kontenera. `dotnet` Polecenie w obrazie środowiska uruchomieniowego może uruchamiać tylko pliki dll. |

### <a name="https-in-docker"></a>HTTPS w Docker

Obrazy podstawowe firmy Microsoft dla platformy Docker ustawiają `ASPNETCORE_URLS` `http://+:80`zmienną środowiskową, co oznacza, że Kestrel będzie działać bez protokołu HTTPS na tym porcie. Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w [poprzedniej sekcji](self-hosted.md)), należy to zastąpić przez ustawienie zmiennej środowiskowej **w części Tworzenie obrazu czasu wykonywania w** pliku dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Plik. dockerignore

Podobnie jak `.gitignore` pliki, które wykluczają pewne pliki i katalogi z kontroli `.dockerignore` źródła, można użyć pliku do wykluczenia plików i katalogów z kopiowania do obrazu podczas kompilacji. To nie tylko zapisuje kopiowanie czasu, ale można również uniknąć błędów powodujących pomyłkę, które powstały w wyniku `obj` (zwłaszcza), że katalog z komputera jest kopiowany do obrazu. Należy dodać co najmniej wpisy dla `bin` i `obj` do `.dockerignore` pliku.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Kompilowanie obrazu

W przypadku rozwiązania z pojedynczą aplikacją, a tym samym pliku dockerfile, najprostszą jest umieszczenie pliku dockerfile w katalogu podstawowym; to jest ten sam katalog `.sln` , w którym znajduje się plik. W takim przypadku, aby skompilować obraz, użyj następującego `docker build` polecenia w katalogu zawierającym pliku dockerfile.

```console
docker build --tag stockdata .
```

Flaga o niewłaściwej nazwie `--tag` (którą można skrócić do `-t`) określa pełną nazwę obrazu, w *tym* rzeczywisty tag, jeśli został określony. Na końcu określa *kontekst* , w którym kompilacja zostanie uruchomiona; bieżący katalog `COPY` roboczy dla poleceń w pliku dockerfile. `.`

Jeśli masz wiele aplikacji w ramach jednego rozwiązania, możesz zachować pliku dockerfile dla każdej aplikacji w swoim folderze, obok `.csproj` pliku, ale nadal powinno być `docker build` uruchomione polecenie z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu. Można określić pliku dockerfile poniżej bieżącego katalogu przy użyciu `--file` flagi (lub `-f`).

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Uruchamianie obrazu w kontenerze na maszynie

Aby uruchomić obraz w lokalnym wystąpieniu platformy Docker, użyj `docker run` polecenia.

```console
docker run -ti -p 5000:80 stockdata
```

`-ti` Flaga łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym. Port `-p 5000:80` "publishs" (linki) 80 w kontenerze do portu 80 w interfejsie sieciowym hosta lokalnego.

## <a name="push-the-image-to-a-registry"></a>Wypchnij obraz do rejestru

Po zweryfikowaniu, że obraz działa, należy wypchnąć go do rejestru platformy Docker, aby udostępnić go w innych systemach. Sieci wewnętrzne muszą obsługiwać rejestr platformy Docker. Może to być tak proste, jak uruchamianie [własnego `registry` obrazu platformy Docker](https://docs.docker.com/registry/deploying/) (to oznacza, że rejestr platformy Docker działa w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania. W przypadku udostępniania zewnętrznego i używania w chmurze dostępne są różne rejestry zarządzane, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub usługa [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Aby wypchnąć do centrum Docker, poprzedź nazwę obrazu nazwą użytkownika lub organizacji.

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

Aby wypchnąć do rejestru prywatnego, prefiks nazwy obrazu z nazwą hosta rejestru i nazwą organizacji.

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

Gdy obraz znajduje się w rejestrze, można wdrożyć go na poszczególnych hostach platformy Docker lub w aparacie aranżacji kontenera, takim jak Kubernetes.

>[!div class="step-by-step"]
>[Poprzedni](self-hosted.md)
>[Następny](kubernetes.md)
