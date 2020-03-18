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
# <a name="create-docker-images"></a><span data-ttu-id="dc288-103">Tworzenie obrazów platformy Docker</span><span class="sxs-lookup"><span data-stu-id="dc288-103">Create Docker images</span></span>

<span data-ttu-id="dc288-104">Ta sekcja obejmuje tworzenie obrazów platformy Docker dla ASP.NET podstawowych aplikacji gRPC, gotowych do pracy w platformie Docker, Kubernetes lub innych środowiskach kontenerów.</span><span class="sxs-lookup"><span data-stu-id="dc288-104">This section covers the creation of Docker images for ASP.NET Core gRPC applications, ready to run in Docker, Kubernetes, or other container environments.</span></span> <span data-ttu-id="dc288-105">Przykładowa aplikacja używana z ASP.NET podstawową aplikacją sieci web MVC i usługą gRPC jest dostępna w repozytorium [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) w serwisie GitHub.</span><span class="sxs-lookup"><span data-stu-id="dc288-105">The sample application used, with an ASP.NET Core MVC web app and a gRPC service, is available on the [dotnet-architecture/grpc-for-wcf-developers](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) repository on GitHub.</span></span>

## <a name="microsoft-base-images-for-aspnet-core-applications"></a><span data-ttu-id="dc288-106">Obrazy podstawowe firmy Microsoft dla aplikacji ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dc288-106">Microsoft base images for ASP.NET Core applications</span></span>

<span data-ttu-id="dc288-107">Firma Microsoft udostępnia szereg obrazów podstawowych do tworzenia i uruchamiania aplikacji .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc288-107">Microsoft provides a range of base images for building and running .NET Core applications.</span></span> <span data-ttu-id="dc288-108">Aby utworzyć ASP.NET obraz core 3.0, należy użyć dwóch obrazów podstawowych:</span><span class="sxs-lookup"><span data-stu-id="dc288-108">To create an ASP.NET Core 3.0 image, you use two base images:</span></span>

- <span data-ttu-id="dc288-109">Obraz sdk do tworzenia i publikowania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc288-109">An SDK image to build and publish the application.</span></span>
- <span data-ttu-id="dc288-110">Obraz w czasie wykonywania dla wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="dc288-110">A runtime image for deployment.</span></span>

| <span data-ttu-id="dc288-111">Image (Obraz)</span><span class="sxs-lookup"><span data-stu-id="dc288-111">Image</span></span> | <span data-ttu-id="dc288-112">Opis</span><span class="sxs-lookup"><span data-stu-id="dc288-112">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="dc288-113">mcr.microsoft.com/dotnet/core/sdk</span><span class="sxs-lookup"><span data-stu-id="dc288-113">mcr.microsoft.com/dotnet/core/sdk</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-sdk/) | <span data-ttu-id="dc288-114">Do tworzenia `docker build`aplikacji z .</span><span class="sxs-lookup"><span data-stu-id="dc288-114">For building applications with `docker build`.</span></span> <span data-ttu-id="dc288-115">Nie do wykorzystania w produkcji.</span><span class="sxs-lookup"><span data-stu-id="dc288-115">Not to be used in production.</span></span> |
| [<span data-ttu-id="dc288-116">mcr.microsoft.com/dotnet/core/aspnet</span><span class="sxs-lookup"><span data-stu-id="dc288-116">mcr.microsoft.com/dotnet/core/aspnet</span></span>](https://hub.docker.com/_/microsoft-dotnet-core-aspnet/) | <span data-ttu-id="dc288-117">Zawiera zależności runtime i ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc288-117">Contains the runtime and ASP.NET Core dependencies.</span></span> <span data-ttu-id="dc288-118">Do produkcji.</span><span class="sxs-lookup"><span data-stu-id="dc288-118">For production.</span></span> |

<span data-ttu-id="dc288-119">Dla każdego obrazu istnieją cztery warianty oparte na różnych dystrybucjach Linuksa, wyróżniające się tagami.</span><span class="sxs-lookup"><span data-stu-id="dc288-119">For each image, there are four variants based on different Linux distributions, distinguished by tags.</span></span>

| <span data-ttu-id="dc288-120">Znaczniki obrazu</span><span class="sxs-lookup"><span data-stu-id="dc288-120">Image tag(s)</span></span> | <span data-ttu-id="dc288-121">Linux</span><span class="sxs-lookup"><span data-stu-id="dc288-121">Linux</span></span> | <span data-ttu-id="dc288-122">Uwagi</span><span class="sxs-lookup"><span data-stu-id="dc288-122">Notes</span></span> |
| --------- | ----- | ----- |
| <span data-ttu-id="dc288-123">3.0-buster, 3.0</span><span class="sxs-lookup"><span data-stu-id="dc288-123">3.0-buster, 3.0</span></span> | <span data-ttu-id="dc288-124">Debian 10</span><span class="sxs-lookup"><span data-stu-id="dc288-124">Debian 10</span></span> | <span data-ttu-id="dc288-125">Domyślny obraz, jeśli nie określono wariantu os.</span><span class="sxs-lookup"><span data-stu-id="dc288-125">The default image if no OS variant is specified.</span></span> |
| <span data-ttu-id="dc288-126">3.0-alpejski</span><span class="sxs-lookup"><span data-stu-id="dc288-126">3.0-alpine</span></span> | <span data-ttu-id="dc288-127">Alpejski 3,9</span><span class="sxs-lookup"><span data-stu-id="dc288-127">Alpine 3.9</span></span> | <span data-ttu-id="dc288-128">Alpejskie obrazy bazowe są znacznie mniejsze niż obrazy Debiana lub Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dc288-128">Alpine base images are much smaller than Debian or Ubuntu ones.</span></span> |
| <span data-ttu-id="dc288-129">3.0-dyskoteka</span><span class="sxs-lookup"><span data-stu-id="dc288-129">3.0-disco</span></span> | <span data-ttu-id="dc288-130">Ubuntu 19.04</span><span class="sxs-lookup"><span data-stu-id="dc288-130">Ubuntu 19.04</span></span> | |
| <span data-ttu-id="dc288-131">3.0-bionic</span><span class="sxs-lookup"><span data-stu-id="dc288-131">3.0-bionic</span></span> | <span data-ttu-id="dc288-132">Ubuntu 18.04</span><span class="sxs-lookup"><span data-stu-id="dc288-132">Ubuntu 18.04</span></span> | |

<span data-ttu-id="dc288-133">Alpejski obraz bazowy wynosi około 100 MB, w porównaniu do 200 MB dla obrazów Debiana i Ubuntu.</span><span class="sxs-lookup"><span data-stu-id="dc288-133">The Alpine base image is around 100 MB, compared to 200 MB for the Debian and Ubuntu images.</span></span> <span data-ttu-id="dc288-134">Niektóre pakiety oprogramowania lub biblioteki mogą nie być dostępne w zarządzaniu pakietami firmy Alpine.</span><span class="sxs-lookup"><span data-stu-id="dc288-134">Some software packages or libraries might not be available in Alpine's package management.</span></span> <span data-ttu-id="dc288-135">Jeśli nie masz pewności, którego obrazu użyć, prawdopodobnie powinieneś wybrać domyślnego Debiana.</span><span class="sxs-lookup"><span data-stu-id="dc288-135">If you're not sure which image to use, you should probably choose the default Debian.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc288-136">Upewnij się, że używasz tego samego wariantu systemu Linux dla kompilacji i w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc288-136">Make sure you use the same variant of Linux for the build and the runtime.</span></span> <span data-ttu-id="dc288-137">Aplikacje utworzone i opublikowane w jednym wariancie mogą nie działać na innym.</span><span class="sxs-lookup"><span data-stu-id="dc288-137">Applications built and published on one variant might not work on another.</span></span>

## <a name="create-a-docker-image"></a><span data-ttu-id="dc288-138">Tworzenie obrazu platformy Docker</span><span class="sxs-lookup"><span data-stu-id="dc288-138">Create a Docker image</span></span>

<span data-ttu-id="dc288-139">Obraz platformy Docker jest definiowany przez *plik Dockerfile*.</span><span class="sxs-lookup"><span data-stu-id="dc288-139">A Docker image is defined by a *Dockerfile*.</span></span> <span data-ttu-id="dc288-140">Jest to plik tekstowy, który zawiera wszystkie polecenia potrzebne do tworzenia aplikacji i instalowania wszelkich zależności, które są wymagane do tworzenia lub uruchamiania aplikacji.</span><span class="sxs-lookup"><span data-stu-id="dc288-140">This is a text file that contains all the commands needed to build the application and install any dependencies that are required for either building or running the application.</span></span> <span data-ttu-id="dc288-141">W poniższym przykładzie przedstawiono najprostszy plik Dockerfile dla ASP.NET aplikacji Core 3.0:</span><span class="sxs-lookup"><span data-stu-id="dc288-141">The following example shows the simplest Dockerfile for an ASP.NET Core 3.0 application:</span></span>

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

<span data-ttu-id="dc288-142">Plik Dockerfile składa się z `sdk` dwóch części: pierwszy używa obrazu podstawowego do tworzenia i publikowania aplikacji; drugi tworzy obraz czasu wykonywania `aspnet` z podstawy.</span><span class="sxs-lookup"><span data-stu-id="dc288-142">The Dockerfile has two parts: the first uses the `sdk` base image to build and publish the application; the second creates a runtime image from the `aspnet` base.</span></span> <span data-ttu-id="dc288-143">Jest tak, `sdk` ponieważ obraz jest około 900 MB, w porównaniu do około 200 MB dla obrazu w czasie wykonywania, a większość jego zawartości są niepotrzebne w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="dc288-143">This is because the `sdk` image is around 900 MB, compared to around 200 MB for the runtime image, and most of its contents are unnecessary at runtime.</span></span>

### <a name="the-build-steps"></a><span data-ttu-id="dc288-144">Kroki kompilacji</span><span class="sxs-lookup"><span data-stu-id="dc288-144">The build steps</span></span>

| <span data-ttu-id="dc288-145">Krok</span><span class="sxs-lookup"><span data-stu-id="dc288-145">Step</span></span> | <span data-ttu-id="dc288-146">Opis</span><span class="sxs-lookup"><span data-stu-id="dc288-146">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="dc288-147">Deklaruje obraz podstawowy i przypisuje `builder` alias.</span><span class="sxs-lookup"><span data-stu-id="dc288-147">Declares the base image and assigns the `builder` alias.</span></span> |
| `WORKDIR /src` | <span data-ttu-id="dc288-148">Tworzy `/src` katalog i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="dc288-148">Creates the `/src` directory and sets it as the current working directory.</span></span> |
| `COPY . .` | <span data-ttu-id="dc288-149">Kopiuje wszystko poniżej bieżącego katalogu na hoście do bieżącego katalogu na obrazie.</span><span class="sxs-lookup"><span data-stu-id="dc288-149">Copies everything below the current directory on the host into the current directory on the image.</span></span> |
| `RUN dotnet restore` | <span data-ttu-id="dc288-150">Przywraca wszystkie pakiety zewnętrzne (ASP.NET framework Core 3.0 jest preinstalowany z zestawem SDK).</span><span class="sxs-lookup"><span data-stu-id="dc288-150">Restores any external packages (ASP.NET Core 3.0 framework is pre-installed with the SDK).</span></span> |
| `RUN dotnet publish ...` | <span data-ttu-id="dc288-151">Tworzy i publikuje kompilację wydania.</span><span class="sxs-lookup"><span data-stu-id="dc288-151">Builds and publishes a Release build.</span></span> <span data-ttu-id="dc288-152">Należy pamiętać, że flaga `--runtime` nie jest wymagana.</span><span class="sxs-lookup"><span data-stu-id="dc288-152">Note that the `--runtime` flag isn't required.</span></span> |

### <a name="the-runtime-image-steps"></a><span data-ttu-id="dc288-153">Kroki obrazu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="dc288-153">The runtime image steps</span></span>

| <span data-ttu-id="dc288-154">Krok</span><span class="sxs-lookup"><span data-stu-id="dc288-154">Step</span></span> | <span data-ttu-id="dc288-155">Opis</span><span class="sxs-lookup"><span data-stu-id="dc288-155">Description</span></span> |
| ---- | ----------- |
| `FROM ...` | <span data-ttu-id="dc288-156">Deklaruje nowy obraz podstawowy.</span><span class="sxs-lookup"><span data-stu-id="dc288-156">Declares a new base image.</span></span> |
| `WORKDIR /app` | <span data-ttu-id="dc288-157">Tworzy `/app` katalog i ustawia go jako bieżący katalog roboczy.</span><span class="sxs-lookup"><span data-stu-id="dc288-157">Creates the `/app` directory and sets it as the current working directory.</span></span> |
| `COPY --from=builder ...` | <span data-ttu-id="dc288-158">Kopiuje opublikowaną aplikację z poprzedniego `builder` obrazu, używając `FROM` aliasu z pierwszego wiersza.</span><span class="sxs-lookup"><span data-stu-id="dc288-158">Copies the published application from the previous image, by using the `builder` alias from the first `FROM` line.</span></span> |
| `ENTRYPOINT [ ... ]` | <span data-ttu-id="dc288-159">Ustawia polecenie do uruchomienia po uruchomieniu kontenera.</span><span class="sxs-lookup"><span data-stu-id="dc288-159">Sets the command to run when the container starts.</span></span> <span data-ttu-id="dc288-160">Polecenie `dotnet` w obrazie w czasie wykonywania można uruchamiać tylko pliki DLL.</span><span class="sxs-lookup"><span data-stu-id="dc288-160">The `dotnet` command in the runtime image can only run DLL files.</span></span> |

### <a name="https-in-docker"></a><span data-ttu-id="dc288-161">HTTPS w platformie Docker</span><span class="sxs-lookup"><span data-stu-id="dc288-161">HTTPS in Docker</span></span>

<span data-ttu-id="dc288-162">Obrazy podstawowe firmy Microsoft `ASPNETCORE_URLS` dla platformy Docker ustawiono zmienną środowiskową na `http://+:80`, co oznacza, że Kestrel działa bez protokołu HTTPS na tym porcie.</span><span class="sxs-lookup"><span data-stu-id="dc288-162">Microsoft base images for Docker set the `ASPNETCORE_URLS` environment variable to `http://+:80`, meaning that Kestrel runs without HTTPS on that port.</span></span> <span data-ttu-id="dc288-163">Jeśli używasz protokołu HTTPS z certyfikatem niestandardowym (zgodnie z opisem w [aplikacjach gRPC hostowanych](self-hosted.md)samodzielnie ), należy to zastąpić.</span><span class="sxs-lookup"><span data-stu-id="dc288-163">If you're using HTTPS with a custom certificate (as described in [Self-hosted gRPC applications](self-hosted.md)), you should override this.</span></span> <span data-ttu-id="dc288-164">Ustaw zmienną środowiskową w części tworzenia obrazu środowiska uruchomieniowego pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dc288-164">Set the environment variable in the runtime image creation part of your Dockerfile.</span></span>

```dockerfile
# Runtime image creation
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0

ENV ASPNETCORE_URLS=https://+:443
```

### <a name="the-dockerignore-file"></a><span data-ttu-id="dc288-165">Plik .dockerignore</span><span class="sxs-lookup"><span data-stu-id="dc288-165">The .dockerignore file</span></span>

<span data-ttu-id="dc288-166">Podobnie `.gitignore` jak pliki, które wykluczają niektóre pliki `.dockerignore` i katalogi z kontroli źródła, plik może służyć do wykluczenia plików i katalogów z kopiowania do obrazu podczas kompilacji.</span><span class="sxs-lookup"><span data-stu-id="dc288-166">Much like `.gitignore` files that exclude certain files and directories from source control, the `.dockerignore` file can be used to exclude files and directories from being copied to the image during build.</span></span> <span data-ttu-id="dc288-167">Pozwala to nie tylko zaoszczędzić czas kopiowania, ale także `obj` uniknąć pewnych błędów wynikających z kopiowania katalogu z komputera do obrazu.</span><span class="sxs-lookup"><span data-stu-id="dc288-167">This not only saves time copying, but can also avoid some errors that arise from having the `obj` directory from your PC copied into the image.</span></span> <span data-ttu-id="dc288-168">Co najmniej należy dodać wpisy `bin` dla `obj` i `.dockerignore` do pliku.</span><span class="sxs-lookup"><span data-stu-id="dc288-168">At a minimum, you should add entries for `bin` and `obj` to your `.dockerignore` file.</span></span>

```console
bin/
obj/
```

## <a name="build-the-image"></a><span data-ttu-id="dc288-169">Tworzenie obrazu</span><span class="sxs-lookup"><span data-stu-id="dc288-169">Build the image</span></span>

<span data-ttu-id="dc288-170">Dla rozwiązania z jednej aplikacji, a tym samym jeden plik Dockerfile, jest najprostszym umieścić Plik Dockerfile w katalogu podstawowym.</span><span class="sxs-lookup"><span data-stu-id="dc288-170">For a solution with a single application, and thus a single Dockerfile, it's simplest to put the Dockerfile in the base directory.</span></span> <span data-ttu-id="dc288-171">Innymi słowy, umieść go w tym `.sln` samym katalogu co plik.</span><span class="sxs-lookup"><span data-stu-id="dc288-171">In other words, put it in the same directory as the `.sln` file.</span></span> <span data-ttu-id="dc288-172">W takim przypadku, aby utworzyć obraz, użyj następującego `docker build` polecenia z katalogu zawierającego Plik Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dc288-172">In that case, to build the image, use the following `docker build` command from the directory containing the Dockerfile.</span></span>

```console
docker build --tag stockdata .
```

<span data-ttu-id="dc288-173">Myląco `--tag` nazwana flaga (która może zostać skrócona do `-t`) określa całą nazwę obrazu, w tym rzeczywisty tag, jeśli został określony.</span><span class="sxs-lookup"><span data-stu-id="dc288-173">The confusingly named `--tag` flag (which can be shortened to `-t`) specifies the whole name of the image, including the actual tag if specified.</span></span> <span data-ttu-id="dc288-174">Na `.` końcu określa kontekst, w którym kompilacja zostanie uruchomiony; bieżącego katalogu roboczego `COPY` dla poleceń w pliku Dockerfile.</span><span class="sxs-lookup"><span data-stu-id="dc288-174">The `.` at the end specifies the context in which the build will be run; the current working directory for the `COPY` commands in the Dockerfile.</span></span>

<span data-ttu-id="dc288-175">Jeśli masz wiele aplikacji w ramach jednego rozwiązania, można zachować Dockerfile dla `.csproj` każdej aplikacji w swoim folderze, obok pliku.</span><span class="sxs-lookup"><span data-stu-id="dc288-175">If you have multiple applications within a single solution, you can keep the Dockerfile for each application in its own folder, beside the `.csproj` file.</span></span> <span data-ttu-id="dc288-176">Nadal należy uruchomić `docker build` polecenie z katalogu podstawowego, aby upewnić się, że rozwiązanie i wszystkie projekty są kopiowane do obrazu.</span><span class="sxs-lookup"><span data-stu-id="dc288-176">You should still run the `docker build` command from the base directory to ensure that the solution and all the projects are copied into the image.</span></span> <span data-ttu-id="dc288-177">Plik dockerfile można określić poniżej bieżącego `--file` katalogu, używając flagi (lub `-f`) .</span><span class="sxs-lookup"><span data-stu-id="dc288-177">You can specify a Dockerfile below the current directory by using the `--file` (or `-f`) flag.</span></span>

```console
docker build --tag stockdata --file src/StockData/Dockerfile .
```

## <a name="run-the-image-in-a-container-on-your-machine"></a><span data-ttu-id="dc288-178">Uruchamianie obrazu w kontenerze na komputerze</span><span class="sxs-lookup"><span data-stu-id="dc288-178">Run the image in a container on your machine</span></span>

<span data-ttu-id="dc288-179">Aby uruchomić obraz w lokalnym wystąpieniu `docker run` platformy Docker, użyj tego polecenia.</span><span class="sxs-lookup"><span data-stu-id="dc288-179">To run the image in your local Docker instance, use the `docker run` command.</span></span>

```console
docker run -ti -p 5000:80 stockdata
```

<span data-ttu-id="dc288-180">Flaga `-ti` łączy bieżący terminal z terminalem kontenera i działa w trybie interaktywnym.</span><span class="sxs-lookup"><span data-stu-id="dc288-180">The `-ti` flag connects your current terminal to the container's terminal, and runs in interactive mode.</span></span> <span data-ttu-id="dc288-181">Publikuje `-p 5000:80` (łączy) port 80 w kontenerze do portu 5000 w interfejsie sieci localhost.</span><span class="sxs-lookup"><span data-stu-id="dc288-181">The `-p 5000:80` publishes (links) port 80 on the container to port 5000 on the localhost network interface.</span></span>

## <a name="push-the-image-to-a-registry"></a><span data-ttu-id="dc288-182">Wypychanie obrazu do rejestru</span><span class="sxs-lookup"><span data-stu-id="dc288-182">Push the image to a registry</span></span>

<span data-ttu-id="dc288-183">Po sprawdzoniu, że obraz działa, wypchnij go do rejestru platformy Docker, aby udostępnić go w innych systemach.</span><span class="sxs-lookup"><span data-stu-id="dc288-183">After you've verified that the image works, push it to a Docker registry to make it available on other systems.</span></span> <span data-ttu-id="dc288-184">Sieci wewnętrzne będą musiały aprowizować rejestr platformy Docker.</span><span class="sxs-lookup"><span data-stu-id="dc288-184">Internal networks will need to provision a Docker registry.</span></span> <span data-ttu-id="dc288-185">Może to być tak proste, jak uruchamianie [własnego `registry` obrazu platformy Docker](https://docs.docker.com/registry/deploying/) (rejestr platformy Docker jest uruchamiany w kontenerze platformy Docker), ale dostępne są różne bardziej kompleksowe rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="dc288-185">This can be as simple as running [Docker's own `registry` image](https://docs.docker.com/registry/deploying/) (the Docker registry runs in a Docker container), but there are various more comprehensive solutions available.</span></span> <span data-ttu-id="dc288-186">Do udostępniania zewnętrznego i korzystania z chmury dostępne są różne zarządzane rejestry, takie jak [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) lub [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span><span class="sxs-lookup"><span data-stu-id="dc288-186">For external sharing and cloud use, there are various managed registries available, such as [Azure Container Registry](https://docs.microsoft.com/azure/container-registry/) or [Docker Hub](https://docs.docker.com/docker-hub/repos/).</span></span>

<span data-ttu-id="dc288-187">Aby wypchnąć do centrum docker, prefiks nazwy obrazu z nazwą użytkownika lub organizacji.</span><span class="sxs-lookup"><span data-stu-id="dc288-187">To push to Docker Hub, prefix the image name with your user or organization name.</span></span>

```console
docker tag stockdata myorg/stockdata
docker push myorg/stockdata
```

<span data-ttu-id="dc288-188">Aby wypchnąć do rejestru prywatnego, prefiks nazwy obrazu z nazwą hosta rejestru i nazwą organizacji.</span><span class="sxs-lookup"><span data-stu-id="dc288-188">To push to a private registry, prefix the image name with the registry host name and the organization name.</span></span>

```console
docker tag stockdata internal-registry:5000/myorg/stockdata
docker push internal-registry:5000/myorg/stockdata
```

<span data-ttu-id="dc288-189">Po obraz znajduje się w rejestrze, można wdrożyć go do poszczególnych hostów platformy Docker lub do aparatu aranżacji kontenerów, takich jak Kubernetes.</span><span class="sxs-lookup"><span data-stu-id="dc288-189">After the image is in a registry, you can deploy it to individual Docker hosts, or to a container orchestration engine like Kubernetes.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="dc288-190">[Poprzedni](self-hosted.md)
>[następny](kubernetes.md)</span><span class="sxs-lookup"><span data-stu-id="dc288-190">[Previous](self-hosted.md)
[Next](kubernetes.md)</span></span>
