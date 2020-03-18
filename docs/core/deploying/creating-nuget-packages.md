---
title: Tworzenie pakietu NuGet za pomocą cli .NET Core
description: Dowiedz się, jak utworzyć pakiet NuGet za pomocą polecenia "dotnet pack".
author: cartermp
ms.date: 06/20/2016
ms.technology: dotnet-cli
ms.openlocfilehash: 3f8e75a501cfc48e1c416f71e91290cab1a4ffae
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76920918"
---
# <a name="how-to-create-a-nuget-package-with-the-net-core-cli"></a><span data-ttu-id="f26cc-103">Jak utworzyć pakiet NuGet za pomocą cli .NET Core</span><span class="sxs-lookup"><span data-stu-id="f26cc-103">How to create a NuGet package with the .NET Core CLI</span></span>

> [!NOTE]
> <span data-ttu-id="f26cc-104">Poniżej przedstawiono przykłady wiersza polecenia przy użyciu systemu Unix.</span><span class="sxs-lookup"><span data-stu-id="f26cc-104">The following shows command-line samples using Unix.</span></span> <span data-ttu-id="f26cc-105">Polecenie, `dotnet pack` jak pokazano tutaj działa w ten sam sposób w systemie Windows.</span><span class="sxs-lookup"><span data-stu-id="f26cc-105">The `dotnet pack` command as shown here works the same way on Windows.</span></span>

<span data-ttu-id="f26cc-106">Oczekuje się, że biblioteki .NET Standard i .NET Core będą dystrybuowane jako pakiety NuGet.</span><span class="sxs-lookup"><span data-stu-id="f26cc-106">.NET Standard and .NET Core libraries are expected to be distributed as NuGet packages.</span></span> <span data-ttu-id="f26cc-107">Jest to w rzeczywistości, jak wszystkie biblioteki .NET Standard są dystrybuowane i używane.</span><span class="sxs-lookup"><span data-stu-id="f26cc-107">This is in fact how all of the .NET Standard libraries are distributed and consumed.</span></span> <span data-ttu-id="f26cc-108">Najłatwiej to zrobić `dotnet pack` za pomocą polecenia.</span><span class="sxs-lookup"><span data-stu-id="f26cc-108">This is most easily done with the `dotnet pack` command.</span></span>

<span data-ttu-id="f26cc-109">Wyobraź sobie, że właśnie napisał niesamowite nowej biblioteki, które chcesz rozpowszechniać za pomocą NuGet.</span><span class="sxs-lookup"><span data-stu-id="f26cc-109">Imagine that you just wrote an awesome new library that you would like to distribute over NuGet.</span></span> <span data-ttu-id="f26cc-110">Możesz utworzyć pakiet NuGet z narzędziami wieloplatformowymi, aby dokładnie to zrobić!</span><span class="sxs-lookup"><span data-stu-id="f26cc-110">You can create a NuGet package with cross-platform tools to do exactly that!</span></span> <span data-ttu-id="f26cc-111">W poniższym przykładzie przyjęto założenie biblioteki `netstandard1.0`o nazwie **SuperAwesomeLibrary,** która jest przeznaczona dla .</span><span class="sxs-lookup"><span data-stu-id="f26cc-111">The following example assumes a library called **SuperAwesomeLibrary** that targets `netstandard1.0`.</span></span>

<span data-ttu-id="f26cc-112">Jeśli masz zależności przechodnie, oznacza to, że projekt, który zależy od innego pakietu, `dotnet restore` upewnij się, aby przywrócić pakiety dla całego rozwiązania za pomocą polecenia przed utworzeniem pakietu NuGet.</span><span class="sxs-lookup"><span data-stu-id="f26cc-112">If you have transitive dependencies, that is, a project that depends on another package, make sure to restore packages for the entire solution with the `dotnet restore` command before you create a NuGet package.</span></span> <span data-ttu-id="f26cc-113">Niezastosowanie się do tego `dotnet pack` spowoduje, że polecenie nie działa poprawnie.</span><span class="sxs-lookup"><span data-stu-id="f26cc-113">Failing to do so will result in the `dotnet pack` command not working properly.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="f26cc-114">Po przywróceniu pakietów można przejść do katalogu, w którym znajduje się biblioteka:</span><span class="sxs-lookup"><span data-stu-id="f26cc-114">After ensuring packages are restored, you can navigate to the directory where a library lives:</span></span>

```console
cd src/SuperAwesomeLibrary
```

<span data-ttu-id="f26cc-115">Następnie jest to tylko jedno polecenie z wiersza polecenia:</span><span class="sxs-lookup"><span data-stu-id="f26cc-115">Then it's just a single command from the command line:</span></span>

```dotnetcli
dotnet pack
```

<span data-ttu-id="f26cc-116">Folder */bin/Debug* będzie teraz wyglądał tak:</span><span class="sxs-lookup"><span data-stu-id="f26cc-116">Your */bin/Debug* folder will now look like this:</span></span>

```console
$ ls bin/Debug
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="f26cc-117">Spowoduje to wygenerowanie pakietu, który jest zdolny do debugowania.</span><span class="sxs-lookup"><span data-stu-id="f26cc-117">This produces a package that is capable of being debugged.</span></span> <span data-ttu-id="f26cc-118">Jeśli chcesz utworzyć pakiet NuGet z plikami binarnymi wersji, `--configuration` wszystko, co musisz zrobić, to dodać (lub `-c`) przełącznik i używać `release` jako argument.</span><span class="sxs-lookup"><span data-stu-id="f26cc-118">If you want to build a NuGet package with release binaries, all you need to do is add the `--configuration` (or `-c`) switch and use `release` as the argument.</span></span>

```dotnetcli
dotnet pack --configuration release
```

<span data-ttu-id="f26cc-119">Folder */bin* będzie teraz miał folder *wersji* zawierający pakiet NuGet z plikami binarnymi wersji:</span><span class="sxs-lookup"><span data-stu-id="f26cc-119">Your */bin* folder will now have a *release* folder containing your NuGet package with release binaries:</span></span>

```console
$ ls bin/release
netstandard1.0/
SuperAwesomeLibrary.1.0.0.nupkg
SuperAwesomeLibrary.1.0.0.symbols.nupkg
```

<span data-ttu-id="f26cc-120">A teraz masz niezbędne pliki do opublikowania pakietu NuGet!</span><span class="sxs-lookup"><span data-stu-id="f26cc-120">And now you have the necessary files to publish a NuGet package!</span></span>

## <a name="dont-confuse-dotnet-pack-with-dotnet-publish"></a><span data-ttu-id="f26cc-121">Nie myl `dotnet pack` się z`dotnet publish`</span><span class="sxs-lookup"><span data-stu-id="f26cc-121">Don't confuse `dotnet pack` with `dotnet publish`</span></span>

<span data-ttu-id="f26cc-122">Ważne jest, aby pamiętać, że `dotnet publish` w żadnym momencie nie jest to polecenie zaangażowany.</span><span class="sxs-lookup"><span data-stu-id="f26cc-122">It is important to note that at no point is the `dotnet publish` command involved.</span></span> <span data-ttu-id="f26cc-123">Polecenie `dotnet publish` służy do wdrażania aplikacji ze wszystkimi ich zależnościami w tym samym pakiecie — a nie do generowania pakietu NuGet do dystrybucji i używania za pośrednictwem NuGet.</span><span class="sxs-lookup"><span data-stu-id="f26cc-123">The `dotnet publish` command is for deploying applications with all of their dependencies in the same bundle -- not for generating a NuGet package to be distributed and consumed via NuGet.</span></span>

## <a name="see-also"></a><span data-ttu-id="f26cc-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f26cc-124">See also</span></span>

- [<span data-ttu-id="f26cc-125">Szybki start: tworzenie i publikowanie pakietu</span><span class="sxs-lookup"><span data-stu-id="f26cc-125">Quickstart: Create and publish a package</span></span>](/nuget/quickstart/create-and-publish-a-package-using-the-dotnet-cli)
