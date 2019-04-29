---
title: Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania
description: Dowiedz się, jak uruchomić testy na opublikowane bibliotek, zamiast w kodzie źródłowym, za pomocą polecenia dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 660b966c6d02353b855e5728094083042a561558
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61665822"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="9e2b8-103">Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania</span><span class="sxs-lookup"><span data-stu-id="9e2b8-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="9e2b8-104">Można uruchomić testy na już opublikowane dane wyjściowe, za pomocą `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="9e2b8-105">Funkcja będzie działać na xUnit, MSTest i NUnit testów.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="9e2b8-106">Po prostu zlokalizuj plik DLL, które było częścią opublikowane dane wyjściowe i uruchom:</span><span class="sxs-lookup"><span data-stu-id="9e2b8-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="9e2b8-107">gdzie `<MyPublishedTests>` jest nazwą projektu testowego opublikowane.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="9e2b8-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e2b8-108">Example</span></span>

<span data-ttu-id="9e2b8-109">Poniższe polecenia pokazują, Uruchamianie testów w opublikowanej pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-109">The commands below demonstrate running tests on a published DLL.</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="9e2b8-110">Uwaga: Jeśli aplikacja jest przeznaczony dla struktury w innych niż `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia, przekazując docelowej platformy framework za pomocą flagi framework.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="9e2b8-111">Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="9e2b8-112">W programie Visual Studio 2017 Update 5 żądaną framework jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9e2b8-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="9e2b8-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9e2b8-113">See also</span></span>

- [<span data-ttu-id="9e2b8-114">Testowanie jednostek za pomocą polecenia dotnet test i struktury xUnit</span><span class="sxs-lookup"><span data-stu-id="9e2b8-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="9e2b8-115">Testowanie jednostek za pomocą polecenia dotnet test i NUnit</span><span class="sxs-lookup"><span data-stu-id="9e2b8-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="9e2b8-116">Testowanie jednostek za pomocą polecenia dotnet test i struktury MSTest</span><span class="sxs-lookup"><span data-stu-id="9e2b8-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
