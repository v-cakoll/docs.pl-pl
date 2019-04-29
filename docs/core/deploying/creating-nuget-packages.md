---
title: Utwórz pakiet NuGet za pomocą narzędzi interfejsu wiersza polecenia (CLI) platformy .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "pakietu dotnet".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.custom: seodec18
ms.openlocfilehash: 1add3470799b75ebb92c67eed3509523e510ab6c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61650898"
---
# <a name="how-to-create-a-nuget-package-with-net-core-command-line-interface-cli-tools"></a><span data-ttu-id="0982d-103">Jak utworzyć pakiet NuGet za pomocą narzędzia interfejsu wiersza polecenia (CLI) platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="0982d-103">How to create a NuGet package with .NET Core command-line interface (CLI) tools</span></span>

> [!NOTE]
> <span data-ttu-id="0982d-104">Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix.</span><span class="sxs-lookup"><span data-stu-id="0982d-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="0982d-105">`dotnet pack` Polecenia, jak pokazano poniżej na Windows działa tak samo.</span><span class="sxs-lookup"><span data-stu-id="0982d-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="0982d-106">Powinny być dystrybuowane jako pakiety NuGet biblioteki .NET standard i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0982d-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="0982d-107">Jest to w rzeczywistości, jak wszystkie biblioteki .NET Standard rozproszone i używane.</span><span class="sxs-lookup"><span data-stu-id="0982d-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="0982d-108">Łatwo to zrobić za pomocą `dotnet pack` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0982d-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="0982d-109">Wyobraź sobie, napisany właśnie awesome nowej biblioteki, które chcesz dystrybuować za pośrednictwem NuGet.</span><span class="sxs-lookup"><span data-stu-id="0982d-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="0982d-110">Można utworzyć pakietu NuGet wraz z tym dokładnie narzędzi międzyplatformowych!</span><span class="sxs-lookup"><span data-stu-id="0982d-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span> <span data-ttu-id="0982d-111">W poniższym przykładzie założono biblioteki, o nazwie **SuperAwesomeLibrary** które elementy docelowe `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="0982d-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="0982d-112">Jeśli masz przechodnie zależności oznacza to, że projekt, który jest zależny od innego pakietu, konieczne będzie upewnij się, że przywracanie pakietów dla całego rozwiązania przy użyciu `dotnet restore` polecenia przed utworzeniem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0982d-112">If you have transitive dependencies; that is, a project which depends on another package, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span> <span data-ttu-id="0982d-113">Niepowodzenie w tym spowoduje `dotnet pack` polecenia nie będą działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="0982d-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="0982d-114">Po upewnieniu się, pakiety zostaną przywrócone, możesz przejść do katalogu, w którym przebywa biblioteki:</span><span class="sxs-lookup"><span data-stu-id="0982d-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="0982d-115">Następnie jest tylko jednego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="0982d-115">Then it's just a single command from the command line:</span></span>

```console
dotnet pack
```

<span data-ttu-id="0982d-116">Twoje `/bin/Debug` folder będzie teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="0982d-116">Your `/bin/Debug` folder will now look like this:</span></span>

```console
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="0982d-117">Należy pamiętać, pozwoli to osiągnąć pakietu, który jest w stanie debugowane.</span><span class="sxs-lookup"><span data-stu-id="0982d-117">Note that this will produce a package which is capable of being debugged.</span></span> <span data-ttu-id="0982d-118">Jeśli chcesz utworzyć pakiet NuGet przy użyciu wersji plików binarnych, wszystko, czego potrzebujesz, aby zrobić to dodanie `--configuration` (lub `-c`) Przełącz i użyj `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="0982d-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```console
dotnet pack --configuration release
```

<span data-ttu-id="0982d-119">Twoje `/bin` folderu będą teraz mieć `release` folder zawierający pakiet NuGet z plikami binarnymi wersji:</span><span class="sxs-lookup"><span data-stu-id="0982d-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="0982d-120">I czy masz pliki niezbędne do publikowania pakietu NuGet teraz!</span><span class="sxs-lookup"><span data-stu-id="0982d-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="0982d-121">Nie należy mylić `dotnet pack` z `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="0982d-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="0982d-122">Ważne jest, aby pamiętać, że w żadnym punkcie nie jest `dotnet publish` zaangażowane polecenia.</span><span class="sxs-lookup"><span data-stu-id="0982d-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="0982d-123">`dotnet publish` Polecenie służy do wdrażania aplikacji za pomocą wszystkie zależności są tego samego pakietu — nie dla generowania pakietu NuGet do dystrybucji i używane za pośrednictwem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="0982d-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="0982d-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0982d-124">See also</span></span>

- [<span data-ttu-id="0982d-125">Szybki start: Tworzenie i publikowanie pakietu</span><span class="sxs-lookup"><span data-stu-id="0982d-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)