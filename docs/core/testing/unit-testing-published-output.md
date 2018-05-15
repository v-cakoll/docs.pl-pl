---
title: Testowanie opublikowane dane wyjściowe z dotnet vstest
description: Dowiedz się, jak uruchomić testy na opublikowane dane wyjściowe z polecenia vstest dotnet.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: dbce1b6e616916e60e56318b773e8fcecbc55580
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="2de28-103">Testowanie opublikowane dane wyjściowe z dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="2de28-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="2de28-104">Można uruchamiać testy na już opublikowane dane wyjściowe przy użyciu `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="2de28-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="2de28-105">Działa to xUnit, MSTest i NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="2de28-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="2de28-106">Po prostu zlokalizuj plik DLL, które były częścią opublikowane dane wyjściowe i uruchom:</span><span class="sxs-lookup"><span data-stu-id="2de28-106">Simply locate the DLL file that was part of your published output and run:</span></span>

```
dotnet vstest <MyPublishedTests>.dll
```

<span data-ttu-id="2de28-107">gdzie `<MyPublishedTests>` to nazwa projektu testowego opublikowane.</span><span class="sxs-lookup"><span data-stu-id="2de28-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

## <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="2de28-108">Przykład uruchamiania testów na opublikowanych biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="2de28-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> <span data-ttu-id="2de28-109">Uwaga: Jeśli aplikacja jest inny niż przeznaczanie dla platformy `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia przez przekazywanie docelową platformę z flagą framework.</span><span class="sxs-lookup"><span data-stu-id="2de28-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="2de28-110">Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="2de28-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="2de28-111">W programie Visual Studio 2017 aktualizacji 5 żądaną framework jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="2de28-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

## <a name="see-also"></a><span data-ttu-id="2de28-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2de28-112">See also</span></span>
 [<span data-ttu-id="2de28-113">Testowanie jednostkowe za pomocą testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="2de28-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)  
 [<span data-ttu-id="2de28-114">Testowanie jednostkowe za pomocą testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="2de28-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)  
