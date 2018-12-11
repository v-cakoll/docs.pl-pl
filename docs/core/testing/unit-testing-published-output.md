---
title: Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania
description: Dowiedz się, jak uruchomić testy na opublikowane bibliotek, zamiast w kodzie źródłowym, za pomocą polecenia dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9d842f26336d0ddf5375d49676523086bb632684
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239530"
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="8ba97-103">Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania</span><span class="sxs-lookup"><span data-stu-id="8ba97-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="8ba97-104">Można uruchomić testy na już opublikowane dane wyjściowe, za pomocą `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="8ba97-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="8ba97-105">Funkcja będzie działać na xUnit, MSTest i NUnit testów.</span><span class="sxs-lookup"><span data-stu-id="8ba97-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="8ba97-106">Po prostu zlokalizuj plik DLL, które było częścią opublikowane dane wyjściowe i uruchom:</span><span class="sxs-lookup"><span data-stu-id="8ba97-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="8ba97-107">gdzie `<MyPublishedTests>` jest nazwą projektu testowego opublikowane.</span><span class="sxs-lookup"><span data-stu-id="8ba97-107">Where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example"></a><span data-ttu-id="8ba97-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8ba97-108">Example</span></span>

<span data-ttu-id="8ba97-109">Poniższe polecenia pokazują, Uruchamianie testów w opublikowanej pliku DLL.</span><span class="sxs-lookup"><span data-stu-id="8ba97-109">The commands below demonstrate running tests on a published DLL.</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="8ba97-110">Uwaga: Jeśli aplikacja jest przeznaczony dla struktury w innych niż `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia, przekazując docelowej platformy framework za pomocą flagi framework.</span><span class="sxs-lookup"><span data-stu-id="8ba97-110">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="8ba97-111">Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="8ba97-111">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="8ba97-112">W programie Visual Studio 2017 Update 5 żądaną framework jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="8ba97-112">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ba97-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ba97-113">See also</span></span>
- [<span data-ttu-id="8ba97-114">Testowanie jednostek za pomocą polecenia dotnet test i struktury xUnit</span><span class="sxs-lookup"><span data-stu-id="8ba97-114">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="8ba97-115">Testowanie jednostek za pomocą polecenia dotnet test i NUnit</span><span class="sxs-lookup"><span data-stu-id="8ba97-115">Unit Testing with dotnet test and NUnit</span></span>](unit-testing-with-nunit.md)
- [<span data-ttu-id="8ba97-116">Testowanie jednostek za pomocą polecenia dotnet test i struktury MSTest</span><span class="sxs-lookup"><span data-stu-id="8ba97-116">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
