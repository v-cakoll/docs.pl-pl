---
title: Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania
description: Dowiedz się, jak uruchomić testy na opublikowane dane wyjściowe za pomocą polecenia dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: e99000996f5dfa9f9d4f9b823e36ecbe325da835
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42936029"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania

Można uruchomić testy na już opublikowane dane wyjściowe, za pomocą `dotnet vstest` polecenia. Funkcja będzie działać na xUnit, MSTest i NUnit testów. Po prostu zlokalizuj plik DLL, które było częścią opublikowane dane wyjściowe i uruchom:

```
dotnet vstest <MyPublishedTests>.dll
```

gdzie `<MyPublishedTests>` jest nazwą projektu testowego opublikowane.

## <a name="example-of-running-tests-on-a-published-dll"></a>Przykład uruchamiania testów na opublikowane biblioteki DLL

```
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Uwaga: Jeśli aplikacja jest przeznaczony dla struktury w innych niż `netcoreapp` nadal można uruchomić `dotnet vstest` polecenia, przekazując docelowej platformy framework za pomocą flagi framework. Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 Update 5 żądaną framework jest wykrywany automatycznie.

## <a name="see-also"></a>Zobacz także
- [Testowanie jednostek za pomocą polecenia dotnet test i struktury xUnit](unit-testing-with-dotnet-test.md)
- [Testowanie jednostek za pomocą polecenia dotnet test i NUnit](unit-testing-with-nunit.md)
- [Testowanie jednostek za pomocą polecenia dotnet test i struktury MSTest](unit-testing-with-mstest.md)
