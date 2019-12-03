---
title: Docker-gRPC dla deweloperów WCF
description: Tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC
ms.date: 09/02/2019
ms.openlocfilehash: d23dc46526183b459c36f11bae4def8b1c9b9410
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711303"
---
# <a name="create-docker-images"></a>Tworzenie obrazów platformy Docker

W tej sekcji opisano tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC, gotowych do uruchamiania w środowiskach Docker, Kubernetes i innych kontenerach. Przykładowa aplikacja używana z aplikacją sieci Web ASP.NET Core MVC i usługą gRPC jest dostępna w repozytorium [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.

## <a name="microsoft-base-images-for-aspnet-core-applications"></a>Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core

Firma Microsoft udostępnia wiele podstawowych obrazów do kompilowania i uruchamiania aplikacji platformy .NET Core. Aby utworzyć obraz ASP.NET Core 3,0, należy użyć dwóch obrazów podstawowych: 

- Obraz zestawu SDK do kompilowania i publikowania aplikacji.
- Obraz środowiska uruchomieniowego na potrzeby wdrożenia.

| Obraz | Opis |
| ----- | ----------- |
| [mcr.microsoft.com/dotnet/core/sdk](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | Do kompilowania aplikacji przy użyciu `docker build`. Nie do użycia w środowisku produkcyjnym. |
| [mcr.microsoft.com/dotnet/core/aspnet](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | Zawiera zależności środowiska uruchomieniowego i ASP.NET Core. Dla środowiska produkcyjnego. |

Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach systemu Linux, które różnią się od tagów.

| Tagi obrazu | Linux | Uwagi |
| --------- | ----- | ----- |
| 3,0 – Buster, 3,0 | Debian 10 | Obraz domyślny, jeśli nie określono żadnego wariantu systemu operacyjnego. |
| 3,0 — Alpine | Alpine 3,9 | Obrazy Alpine Base są znacznie mniejsze niż Debian lub Ubuntu. |
| 3,0 – Disco | Ubuntu 19.04 | |
| 3,0 – Bionic | Ubuntu 18,04 | |

Obraz Alpine Base ma około 100 MB, w porównaniu do 200 MB dla obrazów Debian i Ubuntu. Niektóre pakiety lub biblioteki oprogramowania mogą nie być dostępne w zarządzaniu pakietami Alpine. Jeśli nie masz pewności, którego obrazu użyć, prawdopodobnie wybierz domyślną debian.

> [!IMPORTANT]
> Upewnij się, że używasz tego samego wariantu systemu Linux do kompilowania i środowiska uruchomieniowego. Aplikacje skompilowane i opublikowane na jednym z wariantów mogą nie zadziałały na innym.

## <a name="create-a-docker-image"></a>Tworzenie obrazu platformy Docker

Obraz platformy Docker jest definiowany przez *pliku dockerfile*. Jest to plik tekstowy, który zawiera wszystkie polecenia potrzebne do skompilowania aplikacji i zainstalowania wszelkich zależności, które są wymagane do kompilowania lub uruchamiania aplikacji. Poniższy przykład pokazuje najprostszą pliku dockerfile dla aplikacji ASP.NET Core 3,0:

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

Pliku dockerfile ma dwie części: pierwszy używa `sdk` podstawowego obrazu do kompilowania i publikowania aplikacji. Drugi tworzy obraz środowiska uruchomieniowego z bazy `aspnet`. Jest to spowodowane tym, że obraz `sdk` ma około 900 MB, w porównaniu do około 200 MB dla obrazu środowiska uruchomieniowego, a większość jego zawartości jest niepotrzebna w czasie wykonywania.

### <a name="the-build-steps"></a>Kroki kompilacji

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje podstawowy obraz i przypisuje alias `builder`. |
| `WORKDIR /src` | Tworzy katalog `/src` i ustawia go jako bieżący katalog roboczy. |
| `COPY . .` | Kopiuje wszystkie elementy znajdujące się poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie. |
| `RUN dotnet restore` | Przywraca wszystkie pakiety zewnętrzne (ASP.NET Core 3,0 Framework jest wstępnie zainstalowany wraz z zestawem SDK). |
| `RUN dotnet publish ...` | Kompiluje i publikuje kompilację wydania. Należy zauważyć, że flaga `--runtime` nie jest wymagana. |

### <a name="the-runtime-image-steps"></a>Kroki obrazu środowiska uruchomieniowego

| Krok | Opis |
| ---- | ----------- |
| `FROM ...` | Deklaruje nowy obraz podstawowy. |
| `WORKDIR /app` | Tworzy katalog `/app` i ustawia go jako bieżący katalog roboczy. |
| `COPY --from=builder ...` | Kopiuje opublikowaną aplikację z poprzedniego obrazu przy użyciu aliasu `builder` z pierwszej `FROM` wiersza. |
| `ENTRYPOINT [ ... ]` | Ustawia polecenie, które ma być uruchamiane po rozpoczęciu kontenera. Polecenie `dotnet` w obrazie środowiska uruchomieniowego może uruchamiać tylko pliki DLL. |

### <a name="https-in-docker"></a>HTTPS w Docker

Obrazy podstawowe firmy Microsoft dla platformy Docker Ustaw zmienną środowiskową `ASPNETCORE_URLS` na `http://+:80`, co oznacza, że Kestrel działa bez protokołu HTTPS na tym porcie. Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w temacie [samodzielnych aplikacji gRPC](self-hosted.md)), należy to zmienić. Ustaw zmienną środowiskową w części Tworzenie obrazu środowiska uruchomieniowego pliku dockerfile.

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a>Plik. dockerignore

Podobnie jak `.gitignore` plików, które wykluczają pewne pliki i katalogi z kontroli źródła, plik `.dockerignore` może służyć do wykluczania plików i katalogów z kopiowania do obrazu podczas kompilacji. To nie tylko zapisuje kopiowanie czasu, ale można również uniknąć niektórych błędów, które wynikają z tego, że katalog `obj` pochodzący z komputera został skopiowany do obrazu. Należy dodać do pliku `.dockerignore` wpisy dla `bin` i `obj`.

```console
bin/
obj/
```

## <a name="build-the-image"></a>Kompilowanie obrazu

W przypadku rozwiązania z jedną aplikacją, a tym samym pliku dockerfile, najprostszą jest umieszczenie pliku dockerfile w katalogu podstawowym. Innymi słowy należy umieścić je w tym samym katalogu, co plik `.sln`. W takim przypadku, aby skompilować obraz, użyj następującego polecenia `docker build` z katalogu zawierającego pliku dockerfile.

```console
docker build --tag stockdata .
```

Flaga `--tag` o niewłaściwej nazwie (którą można skrócić do `-t`) określa pełną nazwę obrazu, w tym rzeczywisty tag, jeśli został określony. `.` na końcu określa kontekst, w którym kompilacja będzie uruchamiana; bieżący katalog roboczy dla poleceń `COPY` w pliku dockerfile.

Jeśli masz wiele aplikacji w ramach jednego rozwiązania, możesz zachować pliku dockerfile dla każdej aplikacji w swoim folderze, obok pliku `.csproj`. Nadal powinno być uruchamiane `docker build` polecenie z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu. Można określić pliku dockerfile pod bieżącym katalogiem przy użyciu flagi `--file` (lub `-f`).

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a>Uruchamianie obrazu w kontenerze na maszynie

Aby uruchomić obraz w lokalnym wystąpieniu platformy Docker, użyj polecenia `docker run`.

```console
docker run -ti -p 5000:80 stockdata
```

Flaga `-ti` łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym. `-p 5000:80` publikuje (łącza) port 80 w kontenerze do portu 80 w interfejsie sieciowym hosta lokalnego.

## <a name="push-the-image-to-a-registry"></a>Wypchnij obraz do rejestru

Po zweryfikowaniu, że obraz działa, wypchnij go do rejestru platformy Docker, aby udostępnić go w innych systemach. Sieci wewnętrzne muszą obsługiwać rejestr platformy Docker. Może to być tak proste, jak uruchamianie [własnego obrazu `registry` Docker](https://docs.docker.com/registry/deploying/) (rejestr platformy Docker jest uruchamiany w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania. W przypadku udostępniania zewnętrznego i używania w chmurze dostępne są różne rejestry zarządzane, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub usługa [Docker Hub](https://docs.docker.com/docker-hub/repos/).

Aby przeprowadzić wypychanie do centrum platformy Docker, poprzedź nazwę obrazu nazwą użytkownika lub organizacji.

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
>[Poprzednie](self-hosted.md)
>[dalej](kubernetes.md)
