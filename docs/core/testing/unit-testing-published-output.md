---
title: Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet
description: Dowiedz się, jak uruchamiać testy w opublikowanych bibliotekach, a nie w kodzie źródłowym, za pomocą polecenia dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: e4fd25dc9ff30bdfe85cd1167a1dc41ea20a5f80
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72771925"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="6765a-103">Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet</span><span class="sxs-lookup"><span data-stu-id="6765a-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="6765a-104">Można uruchomić testy dla już opublikowanych danych wyjściowych za pomocą polecenia `dotnet vstest`.</span><span class="sxs-lookup"><span data-stu-id="6765a-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="6765a-105">Będzie to działało na testach xUnit, MSTest i NUnit.</span><span class="sxs-lookup"><span data-stu-id="6765a-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="6765a-106">Po prostu zlokalizuj plik DLL, który był częścią opublikowanych danych wyjściowych, i uruchom:</span><span class="sxs-lookup"><span data-stu-id="6765a-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="6765a-107">Gdzie `<MyPublishedTests>` jest nazwą opublikowanego projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="6765a-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="6765a-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="6765a-108">Example</span></span>

<span data-ttu-id="6765a-109">Poniższe polecenia przedstawiają uruchamianie testów w opublikowanej bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="6765a-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="6765a-110">Uwaga: Jeśli aplikacja jest ukierunkowana na platformę inną niż `netcoreapp`, można nadal uruchomić polecenie `dotnet vstest`, przekazując w platformę docelową flagę platformy.</span><span class="sxs-lookup"><span data-stu-id="6765a-110">Note: If your app targets a framework other than `netcoreapp`, you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="6765a-111">Na przykład `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="6765a-111">For example, `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="6765a-112">W programie Visual Studio 2017 Update 5 i nowszych zostanie automatycznie wykryta pożądana struktura.</span><span class="sxs-lookup"><span data-stu-id="6765a-112">In Visual Studio 2017 Update 5 and later, the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="6765a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6765a-113">See also</span></span>

- [<span data-ttu-id="6765a-114">Testowanie jednostkowe za pomocą testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="6765a-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="6765a-115">Testowanie jednostkowe za pomocą testu dotnet i NUnit</span><span class="sxs-lookup"><span data-stu-id="6765a-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="6765a-116">Testowanie jednostkowe za pomocą testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="6765a-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
