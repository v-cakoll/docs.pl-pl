---
title: Utwórz pakiet NuGet przy użyciu interfejs wiersza polecenia platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet Pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: cdf5084648bf5e77970cbfeaa23f1cab3e6e234e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/01/2020
ms.locfileid: "76920918"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a><span data-ttu-id="ff10b-103">Jak utworzyć pakiet NuGet przy użyciu interfejs wiersza polecenia platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ff10b-103">How to create a NuGet package with the .NET Core CLI</span></span>

> [!NOTE]
> <span data-ttu-id="ff10b-104">Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="ff10b-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="ff10b-105">Polecenie `dotnet pack`, jak pokazano w tym miejscu, działa w taki sam sposób w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="ff10b-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="ff10b-106">Biblioteki .NET Standard i .NET Core są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="ff10b-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="ff10b-107">Jest to fakt, że wszystkie .NET Standard biblioteki są dystrybuowane i używane.</span><span class="sxs-lookup"><span data-stu-id="ff10b-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="ff10b-108">Jest to najłatwiej wykonane za pomocą polecenia `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="ff10b-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="ff10b-109">Załóżmy, że właśnie Zapisano nową bibliotekę, którą chcesz dystrybuować za pośrednictwem narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="ff10b-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="ff10b-110">Pakiet NuGet można utworzyć przy użyciu narzędzi międzyplatformowych, aby dokładnie wykonać te czynności.</span><span class="sxs-lookup"><span data-stu-id="ff10b-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="ff10b-111">W poniższym przykładzie przyjęto, że biblioteka o nazwie **SuperAwesomeLibrary** , która jest przeznaczona dla `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="ff10b-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="ff10b-112">Jeśli istnieją zależności przechodnie, czyli projekt zależny od innego pakietu, należy przywrócić pakiety dla całego rozwiązania przy użyciu polecenia `dotnet restore` przed utworzeniem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ff10b-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="ff10b-113">W przeciwnym razie polecenie `dotnet pack` nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="ff10b-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="ff10b-114">Po przywróceniu pakietów możesz przejść do katalogu, w którym przebywa Biblioteka:</span><span class="sxs-lookup"><span data-stu-id="ff10b-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="ff10b-115">Jest to tylko jedno polecenie z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="ff10b-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="ff10b-116">Folder */bin/debug* będzie teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ff10b-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="ff10b-117">Spowoduje to utworzenie pakietu, który może być debugowany.</span><span class="sxs-lookup"><span data-stu-id="ff10b-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="ff10b-118">Jeśli chcesz skompilować pakiet NuGet przy użyciu plików binarnych wydania, wystarczy dodać przełącznik `--configuration` (lub `-c`) i użyć `release` jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="ff10b-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="ff10b-119">Folder */bin.* będzie teraz zawierać folder *wersji* zawierający pakiet NuGet z wydaniami plików binarnych:</span><span class="sxs-lookup"><span data-stu-id="ff10b-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="ff10b-120">Teraz masz wymagane pliki do opublikowania pakietu NuGet!</span><span class="sxs-lookup"><span data-stu-id="ff10b-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="ff10b-121">Nie należy mylić `dotnet pack` z `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="ff10b-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="ff10b-122">Należy pamiętać, że w żadnym momencie nie jest to `dotnet publish` polecenie.</span><span class="sxs-lookup"><span data-stu-id="ff10b-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="ff10b-123">`dotnet publish` polecenie służy do wdrażania aplikacji ze wszystkimi zależnościami w tym samym pakiecie — nie do generowania pakietu NuGet, który ma być dystrybuowany i używany za pośrednictwem programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ff10b-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff10b-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ff10b-124">See also</span></span>

- [<span data-ttu-id="ff10b-125">Szybki Start: Tworzenie i publikowanie pakietu</span><span class="sxs-lookup"><span data-stu-id="ff10b-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
