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
# <a name="test-published-output-with-dotnet-vstest"></a>Opublikowane dane wyjściowe za pomocą polecenia dotnet vstest testowania

Można uruchomić testy na już opublikowane dane wyjściowe, za pomocą `dotnet vstest` polecenia. Funkcja będzie działać na xUnit, MSTest i NUnit testów. Po prostu zlokalizuj plik DLL, które było częścią opublikowane dane wyjściowe i uruchom:

```
dotnet vstest <MyPublishedTests>.dll
```

gdzie `<MyPublishedTests>` jest nazwą projektu testowego opublikowane.

## <a name="example"></a>Przykład

Poniższe polecenia pokazują, Uruchamianie testów w opublikowanej pliku DLL.

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
