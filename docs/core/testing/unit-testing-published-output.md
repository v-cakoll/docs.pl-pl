---
title: Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet
description: Dowiedz się, jak uruchamiać testy w opublikowanych bibliotekach, a nie w kodzie źródłowym, za pomocą polecenia dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117024"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="0a891-103">Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet</span><span class="sxs-lookup"><span data-stu-id="0a891-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="0a891-104">Można uruchomić testy dla już opublikowanych danych wyjściowych za pomocą `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="0a891-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="0a891-105">Będzie to działało na testach xUnit, MSTest i NUnit.</span><span class="sxs-lookup"><span data-stu-id="0a891-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="0a891-106">Po prostu zlokalizuj plik DLL, który był częścią opublikowanych danych wyjściowych, i uruchom:</span><span class="sxs-lookup"><span data-stu-id="0a891-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="0a891-107">Gdzie `<MyPublishedTests>` to nazwa opublikowanego projektu testowego.</span><span class="sxs-lookup"><span data-stu-id="0a891-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="0a891-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a891-108">Example</span></span>

<span data-ttu-id="0a891-109">Poniższe polecenia przedstawiają uruchamianie testów w opublikowanej bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="0a891-109">The commands below demonstrate running tests on a published DLL.</span></span>

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="0a891-110">Uwaga: Jeśli aplikacja jest ukierunkowana na platformę inną `netcoreapp` niż nadal można `dotnet vstest` uruchomić polecenie, przekazując w platformę docelową flagę platformy.</span><span class="sxs-lookup"><span data-stu-id="0a891-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="0a891-111">Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="0a891-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="0a891-112">W programie Visual Studio 2017 Update 5 żądana platforma jest wykrywana automatycznie.</span><span class="sxs-lookup"><span data-stu-id="0a891-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="0a891-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0a891-113">See also</span></span>

- [<span data-ttu-id="0a891-114">Testowanie jednostkowe za pomocą testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="0a891-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="0a891-115">Testowanie jednostkowe za pomocą testu dotnet i NUnit</span><span class="sxs-lookup"><span data-stu-id="0a891-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="0a891-116">Testowanie jednostkowe za pomocą testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="0a891-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
