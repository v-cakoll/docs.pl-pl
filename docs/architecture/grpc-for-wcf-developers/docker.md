---
title: Docker-gRPC dla deweloperów WCF
description: Tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 2ed3e823c83d8f11fb7290ba6c343b4b47e68e0b
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770546"
---
# <a name="docker"></a><span data-ttu-id="a5894-103">Docker</span><span class="sxs-lookup"><span data-stu-id="a5894-103">Docker</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="a5894-104">Ta sekcja będzie obejmować tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC, gotowych do uruchamiania w środowiskach Docker, Kubernetes i innych kontenerach.</span><span class="sxs-lookup"><span data-stu-id="a5894-104">This section will cover the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="a5894-105">Przykładowa aplikacja używana z aplikacją sieci Web ASP.NET Core MVC i usługą gRPC jest dostępna w repozytorium [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="a5894-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="a5894-106">Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a5894-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="a5894-107">Firma Microsoft udostępnia wiele podstawowych obrazów do kompilowania i uruchamiania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5894-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="a5894-108">Do utworzenia obrazu ASP.NET Core 3,0 są używane dwa obrazy podstawowe: obraz zestawu SDK do kompilowania i publikowania aplikacji oraz obraz środowiska uruchomieniowego na potrzeby wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a5894-108">To create an ASP.NET Core 3.0 image, two base images are used: an SDK image to build and publish the application, and a runtime image for deployment.</span></span>

| <span data-ttu-id="a5894-109">Obraz</span><span class="sxs-lookup"><span data-stu-id="a5894-109">Image</span></span> | <span data-ttu-id="a5894-110">Opis</span><span class="sxs-lookup"><span data-stu-id="a5894-110">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="a5894-111">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="a5894-111">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="a5894-112">Do kompilowania aplikacji przy użyciu `docker build`.</span><span class="sxs-lookup"><span data-stu-id="a5894-112">For building applications with `docker build`.</span></span> <span data-ttu-id="a5894-113">Nie do użycia w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a5894-113">Not to be used in production.</span></span> |
| [<span data-ttu-id="a5894-114">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="a5894-114">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="a5894-115">Zawiera zależności środowiska uruchomieniowego i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a5894-115">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="a5894-116">Dla środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a5894-116">For production.</span></span> |

<span data-ttu-id="a5894-117">Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach systemu Linux, które różnią się od tagów.</span><span class="sxs-lookup"><span data-stu-id="a5894-117">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="a5894-118">Tagi obrazu</span><span class="sxs-lookup"><span data-stu-id="a5894-118">Image tag(s)</span></span> | <span data-ttu-id="a5894-119">Linux</span><span class="sxs-lookup"><span data-stu-id="a5894-119">Linux</span></span> | <span data-ttu-id="a5894-120">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5894-120">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="a5894-121">3,0 – Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="a5894-121">3.0-buster, 3.0</span></span> | <span data-ttu-id="a5894-122">Debian 10</span><span class="sxs-lookup"><span data-stu-id="a5894-122">Debian 10</span></span> | <span data-ttu-id="a5894-123">Obraz domyślny, jeśli nie określono żadnego wariantu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a5894-123">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="a5894-124">3,0 — Alpine</span><span class="sxs-lookup"><span data-stu-id="a5894-124">3.0-alpine</span></span> | <span data-ttu-id="a5894-125">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="a5894-125">Alpine 3.9</span></span> | <span data-ttu-id="a5894-126">Obrazy Alpine Base są znacznie mniejsze niż Debian lub Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a5894-126">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="a5894-127">3,0 – Disco</span><span class="sxs-lookup"><span data-stu-id="a5894-127">3.0-disco</span></span> | <span data-ttu-id="a5894-128">Ubuntu 19,04</span><span class="sxs-lookup"><span data-stu-id="a5894-128">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="a5894-129">3,0 – Bionic</span><span class="sxs-lookup"><span data-stu-id="a5894-129">3.0-bionic</span></span> | <span data-ttu-id="a5894-130">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="a5894-130">Ubuntu 18.04</span></span> | |

<span data-ttu-id="a5894-131">Obraz Alpine Base ma około 100 MB, w porównaniu do 200 MB dla obrazów Debian i Ubuntu, ale niektóre pakiety oprogramowania lub biblioteki mogą nie być dostępne w usłudze Alpine Package Management.</span><span class="sxs-lookup"><span data-stu-id="a5894-131">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images, but some software packages or libraries may not be available in Alpine's package management.</span></span> <span data-ttu-id="a5894-132">Jeśli nie masz pewności, którego obrazu użyć, najlepiej naDebian się na domyślne, chyba że masz atrakcyjną potrzebę używania innego dystrybucjiu.</span><span class="sxs-lookup"><span data-stu-id="a5894-132">If you're not sure which image to use, it's best to stick to the default Debian unless you have a compelling need to use a different distro.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a5894-133">Upewnij się, że używasz tego samego wariantu systemu Linux do kompilowania i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a5894-133">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="a5894-134">Aplikacje skompilowane i opublikowane na jednym z wariantów mogą nie zadziałały na innym.</span><span class="sxs-lookup"><span data-stu-id="a5894-134">Applications built and published on one variant may not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="a5894-135">Tworzenie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="a5894-135">Create a Docker image</span></span>

<span data-ttu-id="a5894-136">Obraz platformy Docker jest definiowany przez *pliku dockerfile*, plik tekstowy, który zawiera wszystkie polecenia, które są potrzebne do skompilowania aplikacji i zainstalowania wszelkich zależności, które są wymagane do tworzenia lub uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a5894-136">A Docker image is defined by a *Dockerfile*, a text file that contains all the commands that are needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="a5894-137">Poniższy przykład pokazuje najprostszą pliku dockerfile dla aplikacji ASP.NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="a5894-137">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="a5894-138">Pliku dockerfile ma dwie części: pierwszy używa `sdk` podstawowego obrazu do kompilowania i publikowania aplikacji. Drugi tworzy obraz środowiska uruchomieniowego z bazy `aspnet`.</span><span class="sxs-lookup"><span data-stu-id="a5894-138">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="a5894-139">Jest to spowodowane tym, że obraz `sdk` jest około 900 MB w porównaniu do około 200 MB dla obrazu środowiska uruchomieniowego, a większość jego zawartości jest niepotrzebna w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a5894-139">This is because the `sdk` image is around 900 MB compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="a5894-140">Kroki kompilacji</span><span class="sxs-lookup"><span data-stu-id="a5894-140">The build steps</span></span>

| <span data-ttu-id="a5894-141">Krok</span><span class="sxs-lookup"><span data-stu-id="a5894-141">Step</span></span> | <span data-ttu-id="a5894-142">Opis</span><span class="sxs-lookup"><span data-stu-id="a5894-142">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a5894-143">Deklaruje podstawowy obraz i przypisuje alias `builder` (zobacz następną sekcję dla wyjaśnienia).</span><span class="sxs-lookup"><span data-stu-id="a5894-143">Declares the base image and assigns the `builder` alias (see next section for explanation).</span></span> |
| `WORKDIR /src` | <span data-ttu-id="a5894-144">Tworzy katalog `/src` i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="a5894-144">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="a5894-145">Kopiuje wszystkie elementy znajdujące się poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="a5894-145">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="a5894-146">Przywraca wszystkie pakiety zewnętrzne (ASP.NET Core 3,0 Framework jest wstępnie zainstalowany wraz z zestawem SDK).</span><span class="sxs-lookup"><span data-stu-id="a5894-146">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="a5894-147">Kompiluje i publikuje kompilację wydania.</span><span class="sxs-lookup"><span data-stu-id="a5894-147">Builds and publishes a Release build.</span></span> <span data-ttu-id="a5894-148">Należy zauważyć, że flaga `--runtime` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a5894-148">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="a5894-149">Kroki obrazu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a5894-149">The runtime image steps</span></span>

| <span data-ttu-id="a5894-150">Krok</span><span class="sxs-lookup"><span data-stu-id="a5894-150">Step</span></span> | <span data-ttu-id="a5894-151">Opis</span><span class="sxs-lookup"><span data-stu-id="a5894-151">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a5894-152">Deklaruje nowy obraz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a5894-152">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="a5894-153">Tworzy katalog `/app` i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="a5894-153">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="a5894-154">Kopiuje opublikowaną aplikację z poprzedniego obrazu przy użyciu aliasu `builder` z pierwszej `FROM` wiersza.</span><span class="sxs-lookup"><span data-stu-id="a5894-154">Copies the published application from the previous image, using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="a5894-155">Ustawia polecenie, które ma być uruchamiane po rozpoczęciu kontenera.</span><span class="sxs-lookup"><span data-stu-id="a5894-155">Sets the command to run when the container starts.</span></span> <span data-ttu-id="a5894-156">Polecenie `dotnet` w obrazie środowiska uruchomieniowego może uruchamiać tylko pliki DLL.</span><span class="sxs-lookup"><span data-stu-id="a5894-156">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="a5894-157">HTTPS w Docker</span><span class="sxs-lookup"><span data-stu-id="a5894-157">HTTPS in Docker</span></span>

<span data-ttu-id="a5894-158">Podstawowe obrazy firmy Microsoft dla platformy Docker Ustaw zmienną środowiskową `ASPNETCORE_URLS` na `http://+:80`, co oznacza, że Kestrel będzie działać bez protokołu HTTPS na tym porcie.</span><span class="sxs-lookup"><span data-stu-id="a5894-158">Microsoft's base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel will run without HTTPS on that port.</span></span> <span data-ttu-id="a5894-159">Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w [poprzedniej sekcji](self-hosted.md)), należy to zastąpić przez ustawienie zmiennej środowiskowej **w części Tworzenie obrazu czasu wykonywania w** pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a5894-159">If you're using HTTPS with a custom certificate (as described in [the previous section](self-hosted.md)), you should override this by setting the environment variable **in the runtime image creation part** of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="a5894-160">Plik. dockerignore</span><span class="sxs-lookup"><span data-stu-id="a5894-160">The .dockerignore file</span></span>

<span data-ttu-id="a5894-161">Podobnie jak `.gitignore` plików, które wykluczają pewne pliki i katalogi z kontroli źródła, plik `.dockerignore` może służyć do wykluczania plików i katalogów z kopiowania do obrazu podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a5894-161">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="a5894-162">Pozwala to nie tylko na kopiowanie czasu, ale może również uniknąć błędów powodujących pomyłkę, które powstały w wyniku (zwłaszcza) `obj` katalogu z komputera skopiowanego do obrazu.</span><span class="sxs-lookup"><span data-stu-id="a5894-162">This not only saves time copying, but can also avoid some confusing errors that arise from having (particularly) the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="a5894-163">Należy dodać co najmniej wpisy dla `bin` i `obj` do pliku `.dockerignore`.</span><span class="sxs-lookup"><span data-stu-id="a5894-163">You should add at least entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="a5894-164">Kompilowanie obrazu</span><span class="sxs-lookup"><span data-stu-id="a5894-164">Build the image</span></span>

<span data-ttu-id="a5894-165">W przypadku rozwiązania z pojedynczą aplikacją, a tym samym pliku dockerfile, najprostszą jest umieszczenie pliku dockerfile w katalogu podstawowym; to jest ten sam katalog, który jest plikiem `.sln`.</span><span class="sxs-lookup"><span data-stu-id="a5894-165">For a solution with a single application, and thus a single Dockerfile, it is simplest to put the Dockerfile in the base directory; that is, the same directory as the `.sln` file.</span></span> <span data-ttu-id="a5894-166">W takim przypadku, aby skompilować obraz, użyj następującego polecenia `docker build` z katalogu zawierającego pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a5894-166">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="a5894-167">Flaga `--tag` o niewłaściwej nazwie (którą można skrócić do `-t`) określa pełną nazwę obrazu, w *tym* rzeczywisty tag, jeśli został określony.</span><span class="sxs-lookup"><span data-stu-id="a5894-167">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, *including* the actual tag if specified.</span></span> <span data-ttu-id="a5894-168">@No__t_0 na końcu określa *kontekst* , w którym kompilacja będzie uruchamiana; bieżący katalog roboczy dla poleceń `COPY` w pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a5894-168">The `.` at the end specifies the *context* in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="a5894-169">Jeśli masz wiele aplikacji w ramach jednego rozwiązania, możesz zachować pliku dockerfile dla każdej aplikacji w swoim folderze, obok pliku `.csproj`, ale nadal należy uruchomić polecenie `docker build` z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="a5894-169">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file, but you should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="a5894-170">Można określić pliku dockerfile pod bieżącym katalogiem przy użyciu flagi `--file` (lub `-f`).</span><span class="sxs-lookup"><span data-stu-id="a5894-170">You can specify a Dockerfile below the current directory using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="a5894-171">Uruchamianie obrazu w kontenerze na maszynie</span><span class="sxs-lookup"><span data-stu-id="a5894-171">Run the image in a container on your machine</span></span>

<span data-ttu-id="a5894-172">Aby uruchomić obraz w lokalnym wystąpieniu platformy Docker, użyj polecenia `docker run`.</span><span class="sxs-lookup"><span data-stu-id="a5894-172">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="a5894-173">Flaga `-ti` łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="a5894-173">The `-ti` flag connects your current terminal to the container's terminal and runs in interactive mode.</span></span> <span data-ttu-id="a5894-174">@No__t_0 publikuje (łącza) port 80 w kontenerze do portu 80 w interfejsie sieciowym hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a5894-174">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="a5894-175">Wypchnij obraz do rejestru</span><span class="sxs-lookup"><span data-stu-id="a5894-175">Push the image to a registry</span></span>

<span data-ttu-id="a5894-176">Po zweryfikowaniu, że obraz działa, należy wypchnąć go do rejestru platformy Docker, aby udostępnić go w innych systemach.</span><span class="sxs-lookup"><span data-stu-id="a5894-176">Once you've verified that the image works, you need to push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="a5894-177">Sieci wewnętrzne muszą obsługiwać rejestr platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a5894-177">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="a5894-178">Może to być tak proste, jak uruchamianie [własnego obrazu `registry` Docker](https://docs.docker.com/registry/deploying/) (to prawo, rejestr platformy Docker działa w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a5894-178">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (that's right, the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="a5894-179">W przypadku udostępniania zewnętrznego i używania w chmurze dostępne są różne rejestry zarządzane, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub usługa [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="a5894-179">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="a5894-180">Aby wypchnąć do centrum Docker, poprzedź nazwę obrazu nazwą użytkownika lub organizacji.</span><span class="sxs-lookup"><span data-stu-id="a5894-180">To push to the Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="a5894-181">Aby wypchnąć do rejestru prywatnego, prefiks nazwy obrazu z nazwą hosta rejestru i nazwą organizacji.</span><span class="sxs-lookup"><span data-stu-id="a5894-181">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="a5894-182">Gdy obraz znajduje się w rejestrze, można wdrożyć go na poszczególnych hostach platformy Docker lub w aparacie aranżacji kontenera, takim jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a5894-182">Once the image is in a registry, you can deploy it to individual Docker hosts or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a5894-183">[Poprzedni](self-hosted.md)
>[Następny](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a5894-183">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
