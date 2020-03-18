---
title: Testowanie opublikowanych danych wyjściowych za pomocą dotnet vstest
description: Dowiedz się, jak uruchamiać testy na opublikowanych bibliotekach, a nie na kodzie źródłowym, za pomocą polecenia dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714268"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="6caa0-103">Testowanie opublikowanych danych wyjściowych za pomocą dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="6caa0-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="6caa0-104">Testy można uruchamiać na już opublikowanych danych wyjściowych za pomocą `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="6caa0-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="6caa0-105">Będzie to działać na testach xUnit, MSTest i NUnit.</span><span class="sxs-lookup"><span data-stu-id="6caa0-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="6caa0-106">Wystarczy zlokalizować plik DLL, który był częścią opublikowanego wyjścia i uruchomić:</span><span class="sxs-lookup"><span data-stu-id="6caa0-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="6caa0-107">Gdzie `<MyPublishedTests>` jest nazwa opublikowanego projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6caa0-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="6caa0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6caa0-108">Example</span></span>

<span data-ttu-id="6caa0-109">Poniższe polecenia pokazują uruchomione testy opublikowanej dll.</span><span class="sxs-lookup"><span data-stu-id="6caa0-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="6caa0-110">Uwaga: Jeśli aplikacja jest przeznaczona dla struktury innej niż `netcoreapp`, nadal można uruchomić `dotnet vstest` polecenie, przekazując w ramach docelowej z flagą struktury.</span><span class="sxs-lookup"><span data-stu-id="6caa0-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="6caa0-111">Na przykład `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="6caa0-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="6caa0-112">W programie Visual Studio 2017 Update 5 i nowszych żądana struktura jest automatycznie wykrywana.</span><span class="sxs-lookup"><span data-stu-id="6caa0-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="6caa0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6caa0-113">See also</span></span>

- [<span data-ttu-id="6caa0-114">Testowanie jednostkowe z testem dotnetowym i jednostką xUnit</span><span class="sxs-lookup"><span data-stu-id="6caa0-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="6caa0-115">Testowanie jednostkowe z testem dotnetowym i jednostką NUnit</span><span class="sxs-lookup"><span data-stu-id="6caa0-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="6caa0-116">Testowanie jednostkowe z testem dotnetowym i mstestem</span><span class="sxs-lookup"><span data-stu-id="6caa0-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
