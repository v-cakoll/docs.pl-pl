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
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowane dane wyjściowe z dotnet vstest

Można uruchamiać testy na już opublikowane dane wyjściowe przy użyciu `dotnet vstest` polecenia. Działa to xUnit, MSTest i NUnit testy. Po prostu zlokalizuj plik DLL, które były częścią opublikowane dane wyjściowe i uruchom:
```
dotnet vstest <MyPublishedTests>.dll
```
gdzie `<MyPublishedTests>` to nazwa projektu testowego opublikowane.

### <a name="example-of-running-tests-on-a-published-dll"></a>Przykład uruchamiania testów na opublikowanych biblioteki DLL

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE] Uwaga: Jeśli aplikacja jest inny niż przeznaczanie dla platformy `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia przez przekazywanie docelową platformę z flagą framework. Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 aktualizacji 5 żądaną framework jest wykrywany automatycznie.

### <a name="related-topics"></a>Tematy pokrewne
- [Testowanie jednostkowe za pomocą testu dotnet i xUnit](unit-testing-with-dotnet-test.md)
- [Testowanie jednostkowe za pomocą testu dotnet i MSTest](unit-testing-with-mstest.md)
