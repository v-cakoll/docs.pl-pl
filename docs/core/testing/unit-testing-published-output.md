---
title: Testowanie opublikowanych danych wyjściowych za pomocą dotnet vstest
description: Dowiedz się, jak uruchamiać testy na opublikowanych bibliotekach, a nie na kodzie źródłowym, za pomocą polecenia dotnet vstest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.openlocfilehash: 7618d37782de3a16f1963380bbb56945fb73e8eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714268"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowanych danych wyjściowych za pomocą dotnet vstest

Testy można uruchamiać na już opublikowanych danych wyjściowych za pomocą `dotnet vstest` polecenia. Będzie to działać na testach xUnit, MSTest i NUnit. Wystarczy zlokalizować plik DLL, który był częścią opublikowanego wyjścia i uruchomić:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Gdzie `<MyPublishedTests>` jest nazwa opublikowanego projektu testowego.

## <a name="example"></a>Przykład

Poniższe polecenia pokazują uruchomione testy opublikowanej dll.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Uwaga: Jeśli aplikacja jest przeznaczona dla struktury innej niż `netcoreapp`, nadal można uruchomić `dotnet vstest` polecenie, przekazując w ramach docelowej z flagą struktury. Na przykład `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 Update 5 i nowszych żądana struktura jest automatycznie wykrywana.

## <a name="see-also"></a>Zobacz też

- [Testowanie jednostkowe z testem dotnetowym i jednostką xUnit](unit-testing-with-dotnet-test.md)
- [Testowanie jednostkowe z testem dotnetowym i jednostką NUnit](unit-testing-with-nunit.md)
- [Testowanie jednostkowe z testem dotnetowym i mstestem](unit-testing-with-mstest.md)
