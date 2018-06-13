---
title: Tworzenie pakietu NuGet z wielu narzędzi platformy
description: Dowiedz się, jak utworzyć pakiet NuGet przy użyciu polecenia "dotnet pack".
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 6be94c2e2cef443f69b2d6df7c2d490cb1fb629d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33219459"
---
# <a name="how-to-create-a-nuget-package-with-cross-platform-tools"></a><span data-ttu-id="ba22d-103">Jak utworzyć pakiet NuGet z wielu narzędzi platformy</span><span class="sxs-lookup"><span data-stu-id="ba22d-103">How to Create a NuGet Package with Cross Platform Tools</span></span>

> [!NOTE]
> <span data-ttu-id="ba22d-104">Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix.</span><span class="sxs-lookup"><span data-stu-id="ba22d-104">The following shows command-line samples using Unix.</span></span>  <span data-ttu-id="ba22d-105">`dotnet pack` Polecenia w sposób pokazany poniżej działa tak samo w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="ba22d-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="ba22d-106">.NET Core 1.0 bibliotek powinny być dystrybuowane jako pakietów NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba22d-106">For .NET Core 1.0, libraries are expected to be distributed as NuGet packages.</span></span>  <span data-ttu-id="ba22d-107">W rzeczywistości jest sposób wszystkich bibliotek .NET Standard distributed i używane.</span><span class="sxs-lookup"><span data-stu-id="ba22d-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span>  <span data-ttu-id="ba22d-108">Jest to łatwo zrobić za pomocą `dotnet pack` polecenia.</span><span class="sxs-lookup"><span data-stu-id="ba22d-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="ba22d-109">Załóżmy, po prostu zapisano świetny nowej biblioteki, który chcesz dystrybuować za pośrednictwem NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba22d-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span>  <span data-ttu-id="ba22d-110">Można utworzyć pakietu NuGet z wielu narzędzi platformy w tym dokładnie!</span><span class="sxs-lookup"><span data-stu-id="ba22d-110">You can create a NuGet package with cross platform tools to do exactly that!</span></span>  <span data-ttu-id="ba22d-111">W poniższym przykładzie założono bibliotece o nazwie **SuperAwesomeLibrary** cele, które `netstandard1.0`.</span><span class="sxs-lookup"><span data-stu-id="ba22d-111">The following example assumes a library called **SuperAwesomeLibrary** which targets `netstandard1.0`.</span></span>

<span data-ttu-id="ba22d-112">Jeśli masz przechodnie zależności; oznacza to, że projekt, który jest zależny od innego projektu, konieczne będzie upewnij się, że przywracanie pakietów dla całego rozwiązania z `dotnet restore` polecenia przed utworzeniem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba22d-112">If you have transitive dependencies; that is, a project which depends on another project, you'll need to make sure to restore packages for your entire solution with the `dotnet restore` command before creating a NuGet package.</span></span>  <span data-ttu-id="ba22d-113">Niepowodzenie w tym przypadku spowoduje `dotnet pack` polecenia może nie działać poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ba22d-113">Failing to do so will result in the `dotnet pack` command to not work properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]


<span data-ttu-id="ba22d-114">Po sprawdzeniu, pakiety zostaną przywrócone, można przejść do katalogu, w którym mieszka biblioteki:</span><span class="sxs-lookup"><span data-stu-id="ba22d-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

`$ cd src/SuperAwesomeLibrary`

<span data-ttu-id="ba22d-115">Następnie jest tylko jednego polecenia w wierszu polecenia:</span><span class="sxs-lookup"><span data-stu-id="ba22d-115">Then it's just a single command from the command line:</span></span>
    
`$ dotnet pack`

<span data-ttu-id="ba22d-116">Twoje `/bin/Debug` folder będzie teraz wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="ba22d-116">Your `/bin/Debug` folder will now look like this:</span></span>

```
$ ls bin/Debug

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="ba22d-117">Należy pamiętać, że spowoduje to utworzenie pakietu, który jest w stanie debugowany.</span><span class="sxs-lookup"><span data-stu-id="ba22d-117">Note that this will produce a package which is capable of being debugged.</span></span>  <span data-ttu-id="ba22d-118">Jeśli chcesz utworzyć pakiet NuGet przy użyciu wersji plików binarnych, wszystko co należy zrobić jest dodać `-c` / `--configuration` przełącznika i użyj `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="ba22d-118">If you want to build a NuGet package with release binaries, all you need to do is add the `-c`/`--configuration` switch and use `release` as the argument.</span></span>

`$ dotnet pack --configuration release`

<span data-ttu-id="ba22d-119">Twoje `/bin` folderu mają teraz `release` folderu zawierającego pakiet NuGet przy użyciu wersji plików binarnych:</span><span class="sxs-lookup"><span data-stu-id="ba22d-119">Your `/bin` folder will now have a `release` folder containing your NuGet package with release binaries:</span></span>

```
$ ls bin/release

netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="ba22d-120">I teraz masz pliki niezbędne do publikowania pakietu NuGet!</span><span class="sxs-lookup"><span data-stu-id="ba22d-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="ba22d-121">Nie należy mylić `dotnet pack` z `dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="ba22d-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="ba22d-122">Należy pamiętać, że w żadnym punkcie `dotnet publish` polecenia wykonywane.</span><span class="sxs-lookup"><span data-stu-id="ba22d-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span>  <span data-ttu-id="ba22d-123">`dotnet publish` Polecenie jest do wdrażania aplikacji za pomocą wszystkie zależności w tym samym pakiecie — nie w celu wygenerowania pakietu NuGet w celu można dystrybuować i używane za pośrednictwem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="ba22d-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -  not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>
