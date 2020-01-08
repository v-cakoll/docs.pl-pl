---
title: Tworzenie pakietu NuGet za pomocą interfejs wiersza polecenia platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet Pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 4927e3796be42d70d25a1947d4519312aef7e289
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75343615"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="103fc-103">Jak utworzyć pakiet NuGet przy użyciu narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="103fc-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="103fc-104">Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu UNIX.</span><span class="sxs-lookup"><span data-stu-id="103fc-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="103fc-105">Polecenie `dotnet pack`, jak pokazano w tym miejscu, działa w taki sam sposób w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="103fc-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="103fc-106">Biblioteki .NET Standard i .NET Core są dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="103fc-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="103fc-107">Jest to fakt, że wszystkie .NET Standard biblioteki są dystrybuowane i używane.</span><span class="sxs-lookup"><span data-stu-id="103fc-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="103fc-108">Jest to najłatwiej wykonane za pomocą polecenia `dotnet pack`.</span><span class="sxs-lookup"><span data-stu-id="103fc-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="103fc-109">Załóżmy, że właśnie Zapisano nową bibliotekę, którą chcesz dystrybuować za pośrednictwem narzędzia NuGet.</span><span class="sxs-lookup"><span data-stu-id="103fc-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="103fc-110">Pakiet NuGet można utworzyć przy użyciu narzędzi międzyplatformowych, aby dokładnie wykonać te czynności.</span><span class="sxs-lookup"><span data-stu-id="103fc-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="103fc-111">W poniższym przykładzie przyjęto, że biblioteka o nazwie **SuperAwesomeLibrary** , której elementy docelowe `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="103fc-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="103fc-112">Jeśli istnieją zależności przechodnie; oznacza to, że projekt, który zależy od innego pakietu, należy upewnić się, że pakiety dla całego rozwiązania zostały przywrócone za pomocą polecenia `dotnet restore` przed utworzeniem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="103fc-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="103fc-113">W przeciwnym razie polecenie `dotnet pack` nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="103fc-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="103fc-114">Po przywróceniu pakietów możesz przejść do katalogu, w którym przebywa Biblioteka:</span><span class="sxs-lookup"><span data-stu-id="103fc-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="103fc-115">Jest to tylko jedno polecenie z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="103fc-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="103fc-116">Folder */bin/debug* będzie teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="103fc-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="103fc-117">Należy pamiętać, że spowoduje to utworzenie pakietu, który jest w stanie debugować.</span><span class="sxs-lookup"><span data-stu-id="103fc-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="103fc-118">Jeśli chcesz skompilować pakiet NuGet przy użyciu plików binarnych wydania, wystarczy dodać przełącznik `--configuration` (lub `-c`) i użyć `release` jako argumentu.</span><span class="sxs-lookup"><span data-stu-id="103fc-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="103fc-119">Folder */bin.* będzie teraz zawierać folder *wersji* zawierający pakiet NuGet z wydaniami plików binarnych:</span><span class="sxs-lookup"><span data-stu-id="103fc-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="103fc-120">Teraz masz wymagane pliki do opublikowania pakietu NuGet!</span><span class="sxs-lookup"><span data-stu-id="103fc-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="103fc-121">Nie należy mylić `dotnet pack` z `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="103fc-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="103fc-122">Należy pamiętać, że w żadnym momencie nie jest to `dotnet publish` polecenie.</span><span class="sxs-lookup"><span data-stu-id="103fc-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="103fc-123">`dotnet publish` polecenie służy do wdrażania aplikacji ze wszystkimi zależnościami w tym samym pakiecie — nie do generowania pakietu NuGet, który ma być dystrybuowany i używany za pośrednictwem programu NuGet.</span><span class="sxs-lookup"><span data-stu-id="103fc-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="103fc-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="103fc-124">See also</span></span>

- [<span data-ttu-id="103fc-125">Szybki Start: Tworzenie i publikowanie pakietu</span><span class="sxs-lookup"><span data-stu-id="103fc-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
