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
# <a name="create-docker-images"></a><span data-ttu-id="a9429-103">Tworzenie obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="a9429-103">Create Docker images</span></span>

<span data-ttu-id="a9429-104">W tej sekcji opisano tworzenie obrazów platformy Docker dla ASP.NET Core aplikacji gRPC, gotowych do uruchamiania w środowiskach Docker, Kubernetes i innych kontenerach.</span><span class="sxs-lookup"><span data-stu-id="a9429-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="a9429-105">Przykładowa aplikacja używana z aplikacją sieci Web ASP.NET Core MVC i usługą gRPC jest dostępna w repozytorium [dotnet-Architecture/gRPC-for-WCF-Developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="a9429-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="a9429-106">Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="a9429-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="a9429-107">Firma Microsoft udostępnia wiele podstawowych obrazów do kompilowania i uruchamiania aplikacji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9429-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="a9429-108">Aby utworzyć obraz ASP.NET Core 3,0, należy użyć dwóch obrazów podstawowych:</span><span class="sxs-lookup"><span data-stu-id="a9429-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span> 

- <span data-ttu-id="a9429-109">Obraz zestawu SDK do kompilowania i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9429-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="a9429-110">Obraz środowiska uruchomieniowego na potrzeby wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="a9429-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="a9429-111">Obraz</span><span class="sxs-lookup"><span data-stu-id="a9429-111">Image</span></span> | <span data-ttu-id="a9429-112">Opis</span><span class="sxs-lookup"><span data-stu-id="a9429-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="a9429-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="a9429-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="a9429-114">Do kompilowania aplikacji przy użyciu `docker build`.</span><span class="sxs-lookup"><span data-stu-id="a9429-114">For building applications with `docker build`.</span></span> <span data-ttu-id="a9429-115">Nie do użycia w środowisku produkcyjnym.</span><span class="sxs-lookup"><span data-stu-id="a9429-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="a9429-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="a9429-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="a9429-117">Zawiera zależności środowiska uruchomieniowego i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="a9429-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="a9429-118">Dla środowiska produkcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a9429-118">For production.</span></span> |

<span data-ttu-id="a9429-119">Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach systemu Linux, które różnią się od tagów.</span><span class="sxs-lookup"><span data-stu-id="a9429-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="a9429-120">Tagi obrazu</span><span class="sxs-lookup"><span data-stu-id="a9429-120">Image tag(s)</span></span> | <span data-ttu-id="a9429-121">Linux</span><span class="sxs-lookup"><span data-stu-id="a9429-121">Linux</span></span> | <span data-ttu-id="a9429-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a9429-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="a9429-123">3,0 – Buster, 3,0</span><span class="sxs-lookup"><span data-stu-id="a9429-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="a9429-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="a9429-124">Debian 10</span></span> | <span data-ttu-id="a9429-125">Obraz domyślny, jeśli nie określono żadnego wariantu systemu operacyjnego.</span><span class="sxs-lookup"><span data-stu-id="a9429-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="a9429-126">3,0 — Alpine</span><span class="sxs-lookup"><span data-stu-id="a9429-126">3.0-alpine</span></span> | <span data-ttu-id="a9429-127">Alpine 3,9</span><span class="sxs-lookup"><span data-stu-id="a9429-127">Alpine 3.9</span></span> | <span data-ttu-id="a9429-128">Obrazy Alpine Base są znacznie mniejsze niż Debian lub Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a9429-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="a9429-129">3,0 – Disco</span><span class="sxs-lookup"><span data-stu-id="a9429-129">3.0-disco</span></span> | <span data-ttu-id="a9429-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="a9429-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="a9429-131">3,0 – Bionic</span><span class="sxs-lookup"><span data-stu-id="a9429-131">3.0-bionic</span></span> | <span data-ttu-id="a9429-132">Ubuntu 18,04</span><span class="sxs-lookup"><span data-stu-id="a9429-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="a9429-133">Obraz Alpine Base ma około 100 MB, w porównaniu do 200 MB dla obrazów Debian i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="a9429-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="a9429-134">Niektóre pakiety lub biblioteki oprogramowania mogą nie być dostępne w zarządzaniu pakietami Alpine.</span><span class="sxs-lookup"><span data-stu-id="a9429-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="a9429-135">Jeśli nie masz pewności, którego obrazu użyć, prawdopodobnie wybierz domyślną debian.</span><span class="sxs-lookup"><span data-stu-id="a9429-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a9429-136">Upewnij się, że używasz tego samego wariantu systemu Linux do kompilowania i środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a9429-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="a9429-137">Aplikacje skompilowane i opublikowane na jednym z wariantów mogą nie zadziałały na innym.</span><span class="sxs-lookup"><span data-stu-id="a9429-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="a9429-138">Tworzenie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="a9429-138">Create a Docker image</span></span>

<span data-ttu-id="a9429-139">Obraz platformy Docker jest definiowany przez *pliku dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="a9429-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="a9429-140">Jest to plik tekstowy, który zawiera wszystkie polecenia potrzebne do skompilowania aplikacji i zainstalowania wszelkich zależności, które są wymagane do kompilowania lub uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a9429-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="a9429-141">Poniższy przykład pokazuje najprostszą pliku dockerfile dla aplikacji ASP.NET Core 3,0:</span><span class="sxs-lookup"><span data-stu-id="a9429-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="a9429-142">Pliku dockerfile ma dwie części: pierwszy używa `sdk` podstawowego obrazu do kompilowania i publikowania aplikacji. Drugi tworzy obraz środowiska uruchomieniowego z bazy `aspnet`.</span><span class="sxs-lookup"><span data-stu-id="a9429-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="a9429-143">Jest to spowodowane tym, że obraz `sdk` ma około 900 MB, w porównaniu do około 200 MB dla obrazu środowiska uruchomieniowego, a większość jego zawartości jest niepotrzebna w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="a9429-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="a9429-144">Kroki kompilacji</span><span class="sxs-lookup"><span data-stu-id="a9429-144">The build steps</span></span>

| <span data-ttu-id="a9429-145">Krok</span><span class="sxs-lookup"><span data-stu-id="a9429-145">Step</span></span> | <span data-ttu-id="a9429-146">Opis</span><span class="sxs-lookup"><span data-stu-id="a9429-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a9429-147">Deklaruje podstawowy obraz i przypisuje alias `builder`.</span><span class="sxs-lookup"><span data-stu-id="a9429-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="a9429-148">Tworzy katalog `/src` i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="a9429-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="a9429-149">Kopiuje wszystkie elementy znajdujące się poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="a9429-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="a9429-150">Przywraca wszystkie pakiety zewnętrzne (ASP.NET Core 3,0 Framework jest wstępnie zainstalowany wraz z zestawem SDK).</span><span class="sxs-lookup"><span data-stu-id="a9429-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="a9429-151">Kompiluje i publikuje kompilację wydania.</span><span class="sxs-lookup"><span data-stu-id="a9429-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="a9429-152">Należy zauważyć, że flaga `--runtime` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="a9429-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="a9429-153">Kroki obrazu środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="a9429-153">The runtime image steps</span></span>

| <span data-ttu-id="a9429-154">Krok</span><span class="sxs-lookup"><span data-stu-id="a9429-154">Step</span></span> | <span data-ttu-id="a9429-155">Opis</span><span class="sxs-lookup"><span data-stu-id="a9429-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="a9429-156">Deklaruje nowy obraz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="a9429-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="a9429-157">Tworzy katalog `/app` i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="a9429-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="a9429-158">Kopiuje opublikowaną aplikację z poprzedniego obrazu przy użyciu aliasu `builder` z pierwszej `FROM` wiersza.</span><span class="sxs-lookup"><span data-stu-id="a9429-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="a9429-159">Ustawia polecenie, które ma być uruchamiane po rozpoczęciu kontenera.</span><span class="sxs-lookup"><span data-stu-id="a9429-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="a9429-160">Polecenie `dotnet` w obrazie środowiska uruchomieniowego może uruchamiać tylko pliki DLL.</span><span class="sxs-lookup"><span data-stu-id="a9429-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="a9429-161">HTTPS w Docker</span><span class="sxs-lookup"><span data-stu-id="a9429-161">HTTPS in Docker</span></span>

<span data-ttu-id="a9429-162">Obrazy podstawowe firmy Microsoft dla platformy Docker Ustaw zmienną środowiskową `ASPNETCORE_URLS` na `http://+:80`, co oznacza, że Kestrel działa bez protokołu HTTPS na tym porcie.</span><span class="sxs-lookup"><span data-stu-id="a9429-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="a9429-163">Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w temacie [samodzielnych aplikacji gRPC](self-hosted.md)), należy to zmienić.</span><span class="sxs-lookup"><span data-stu-id="a9429-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="a9429-164">Ustaw zmienną środowiskową w części Tworzenie obrazu środowiska uruchomieniowego pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a9429-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="a9429-165">Plik. dockerignore</span><span class="sxs-lookup"><span data-stu-id="a9429-165">The .dockerignore file</span></span>

<span data-ttu-id="a9429-166">Podobnie jak `.gitignore` plików, które wykluczają pewne pliki i katalogi z kontroli źródła, plik `.dockerignore` może służyć do wykluczania plików i katalogów z kopiowania do obrazu podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="a9429-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="a9429-167">To nie tylko zapisuje kopiowanie czasu, ale można również uniknąć niektórych błędów, które wynikają z tego, że katalog `obj` pochodzący z komputera został skopiowany do obrazu.</span><span class="sxs-lookup"><span data-stu-id="a9429-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="a9429-168">Należy dodać do pliku `.dockerignore` wpisy dla `bin` i `obj`.</span><span class="sxs-lookup"><span data-stu-id="a9429-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="a9429-169">Kompilowanie obrazu</span><span class="sxs-lookup"><span data-stu-id="a9429-169">Build the image</span></span>

<span data-ttu-id="a9429-170">W przypadku rozwiązania z jedną aplikacją, a tym samym pliku dockerfile, najprostszą jest umieszczenie pliku dockerfile w katalogu podstawowym.</span><span class="sxs-lookup"><span data-stu-id="a9429-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="a9429-171">Innymi słowy należy umieścić je w tym samym katalogu, co plik `.sln`.</span><span class="sxs-lookup"><span data-stu-id="a9429-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="a9429-172">W takim przypadku, aby skompilować obraz, użyj następującego polecenia `docker build` z katalogu zawierającego pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a9429-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="a9429-173">Flaga `--tag` o niewłaściwej nazwie (którą można skrócić do `-t`) określa pełną nazwę obrazu, w tym rzeczywisty tag, jeśli został określony.</span><span class="sxs-lookup"><span data-stu-id="a9429-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="a9429-174">`.` na końcu określa kontekst, w którym kompilacja będzie uruchamiana; bieżący katalog roboczy dla poleceń `COPY` w pliku dockerfile.</span><span class="sxs-lookup"><span data-stu-id="a9429-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="a9429-175">Jeśli masz wiele aplikacji w ramach jednego rozwiązania, możesz zachować pliku dockerfile dla każdej aplikacji w swoim folderze, obok pliku `.csproj`.</span><span class="sxs-lookup"><span data-stu-id="a9429-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="a9429-176">Nadal powinno być uruchamiane `docker build` polecenie z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="a9429-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="a9429-177">Można określić pliku dockerfile pod bieżącym katalogiem przy użyciu flagi `--file` (lub `-f`).</span><span class="sxs-lookup"><span data-stu-id="a9429-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="a9429-178">Uruchamianie obrazu w kontenerze na maszynie</span><span class="sxs-lookup"><span data-stu-id="a9429-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="a9429-179">Aby uruchomić obraz w lokalnym wystąpieniu platformy Docker, użyj polecenia `docker run`.</span><span class="sxs-lookup"><span data-stu-id="a9429-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="a9429-180">Flaga `-ti` łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="a9429-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="a9429-181">`-p 5000:80` publikuje (łącza) port 80 w kontenerze do portu 80 w interfejsie sieciowym hosta lokalnego.</span><span class="sxs-lookup"><span data-stu-id="a9429-181">The `-p 5000:80` publishes (links) port 80 on the container to port 80 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="a9429-182">Wypchnij obraz do rejestru</span><span class="sxs-lookup"><span data-stu-id="a9429-182">Push the image to a registry</span></span>

<span data-ttu-id="a9429-183">Po zweryfikowaniu, że obraz działa, wypchnij go do rejestru platformy Docker, aby udostępnić go w innych systemach.</span><span class="sxs-lookup"><span data-stu-id="a9429-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="a9429-184">Sieci wewnętrzne muszą obsługiwać rejestr platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="a9429-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="a9429-185">Może to być tak proste, jak uruchamianie [własnego obrazu `registry` Docker](https://docs.docker.com/registry/deploying/) (rejestr platformy Docker jest uruchamiany w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="a9429-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="a9429-186">W przypadku udostępniania zewnętrznego i używania w chmurze dostępne są różne rejestry zarządzane, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub usługa [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="a9429-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="a9429-187">Aby przeprowadzić wypychanie do centrum platformy Docker, poprzedź nazwę obrazu nazwą użytkownika lub organizacji.</span><span class="sxs-lookup"><span data-stu-id="a9429-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="a9429-188">Aby wypchnąć do rejestru prywatnego, prefiks nazwy obrazu z nazwą hosta rejestru i nazwą organizacji.</span><span class="sxs-lookup"><span data-stu-id="a9429-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="a9429-189">Gdy obraz znajduje się w rejestrze, można wdrożyć go na poszczególnych hostach platformy Docker lub w aparacie aranżacji kontenera, takim jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="a9429-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="a9429-190">[Poprzednie](self-hosted.md)
>[dalej](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="a9429-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
