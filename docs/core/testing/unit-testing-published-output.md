---
title: "Testowanie opublikowane dane wyjściowe z dotnet vstest"
description: "Dowiedz się, jak uruchomić testy na opublikowane dane wyjściowe z polecenia vstest dotnet."
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.topic: article
ms.prod: .net-core
ms.openlocfilehash: 6651d41d4d60194aec035107e3a65df6a5f70a51
ms.sourcegitcommit: 4a96a0fe9f87de70291245d71b76c7d1b15127ae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/17/2017
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowane dane wyjściowe z dotnet vstest

Można uruchamiać testy na już opublikowane dane wyjściowe przy użyciu `dotnet vstest` polecenia. Działa to xUnit, MSTest i NUnit testy. Po prostu zlokalizuj plik DLL, które były częścią opublikowane dane wyjściowe i uruchom:

```
dotnet vstest <MyPublishedTests>.dll
```

gdzie `<MyPublishedTests>` to nazwa projektu testowego opublikowane.

## <a name="example-of-running-tests-on-a-published-dll"></a>Przykład uruchamiania testów na opublikowanych biblioteki DLL

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Uwaga: Jeśli aplikacja jest inny niż przeznaczanie dla platformy `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia przez przekazywanie docelową platformę z flagą framework. Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 aktualizacji 5 żądaną framework jest wykrywany automatycznie.

## <a name="see-also"></a>Zobacz także
 [Testowanie jednostkowe za pomocą testu dotnet i xUnit](unit-testing-with-dotnet-test.md)  
 [Testowanie jednostkowe za pomocą testu dotnet i MSTest](unit-testing-with-mstest.md)  
