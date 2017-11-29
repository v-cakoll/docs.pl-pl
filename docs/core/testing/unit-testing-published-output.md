---
title: "Testowanie opublikowane dane wyjściowe z dotnet vstest"
description: "Dowiedz się, jak uruchomić testy na opublikowane dane wyjściowe z polecenia vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 3965e4ca-75b8-4969-b3af-ca993c397a15
ms.openlocfilehash: 217787d41a9da6000941ded6caaa4f44d124644b
ms.sourcegitcommit: 8a4f8e6a7f1341764abcd188a332cc28d1e2d8ec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/24/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a><span data-ttu-id="7570a-103">Testowanie opublikowane dane wyjściowe z dotnet vstest</span><span class="sxs-lookup"><span data-stu-id="7570a-103">Test published output with dotnet vstest</span></span>

<span data-ttu-id="7570a-104">Można uruchamiać testy na już opublikowane dane wyjściowe przy użyciu `dotnet vstest` polecenia.</span><span class="sxs-lookup"><span data-stu-id="7570a-104">You can run tests on already published output by using the `dotnet vstest` command.</span></span> <span data-ttu-id="7570a-105">Działa to xUnit, MSTest i NUnit testy.</span><span class="sxs-lookup"><span data-stu-id="7570a-105">This will work on xUnit, MSTest, and NUnit tests.</span></span> <span data-ttu-id="7570a-106">Po prostu zlokalizuj plik DLL, które były częścią opublikowane dane wyjściowe i uruchom:</span><span class="sxs-lookup"><span data-stu-id="7570a-106">Simply locate the DLL file that was part of your published output and run:</span></span>
```
dotnet vstest <MyPublishedTests>.dll
```
<span data-ttu-id="7570a-107">gdzie `<MyPublishedTests>` to nazwa projektu testowego opublikowane.</span><span class="sxs-lookup"><span data-stu-id="7570a-107">where `<MyPublishedTests>` is the name of your published test project.</span></span>

### <a name="example-of-running-tests-on-a-published-dll"></a><span data-ttu-id="7570a-108">Przykład uruchamiania testów na opublikowanych biblioteki DLL</span><span class="sxs-lookup"><span data-stu-id="7570a-108">Example of running tests on a published DLL</span></span>

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] <span data-ttu-id="7570a-109">Uwaga: Jeśli aplikacja jest inny niż przeznaczanie dla platformy `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia przez przekazywanie docelową platformę z flagą framework.</span><span class="sxs-lookup"><span data-stu-id="7570a-109">Note: If your app is targeting a framework other than `netcoreapp` you can still run the `dotnet vstest` command by passing in the targeted framework with a framework flag.</span></span> <span data-ttu-id="7570a-110">Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span><span class="sxs-lookup"><span data-stu-id="7570a-110">For example, `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`.</span></span> <span data-ttu-id="7570a-111">W programie Visual Studio 2017 aktualizacji 5 żądaną framework jest wykrywany automatycznie.</span><span class="sxs-lookup"><span data-stu-id="7570a-111">In Visual Studio 2017 Update 5 the desired framework is automatically detected.</span></span>

### <a name="related-topics"></a><span data-ttu-id="7570a-112">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="7570a-112">Related topics</span></span>
- [<span data-ttu-id="7570a-113">Testowanie jednostkowe za pomocą testu dotnet i xUnit</span><span class="sxs-lookup"><span data-stu-id="7570a-113">Unit Testing with dotnet test and xUnit</span></span>](unit-testing-with-dotnet-test.md)
- [<span data-ttu-id="7570a-114">Testowanie jednostkowe za pomocą testu dotnet i MSTest</span><span class="sxs-lookup"><span data-stu-id="7570a-114">Unit Testing with dotnet test and MSTest</span></span>](unit-testing-with-mstest.md)
