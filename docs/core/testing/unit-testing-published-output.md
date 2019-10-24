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
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet

Można uruchomić testy dla już opublikowanych danych wyjściowych za pomocą polecenia `dotnet vstest`. Będzie to działało na testach xUnit, MSTest i NUnit. Po prostu zlokalizuj plik DLL, który był częścią opublikowanych danych wyjściowych, i uruchom:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Gdzie `<MyPublishedTests>` jest nazwą opublikowanego projektu testowego.

## <a name="example"></a>Przykład

Poniższe polecenia przedstawiają uruchamianie testów w opublikowanej bibliotece DLL.

```dotnetcli
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Uwaga: Jeśli aplikacja jest ukierunkowana na platformę inną niż `netcoreapp`, można nadal uruchomić polecenie `dotnet vstest`, przekazując w platformę docelową flagę platformy. Na przykład `dotnet vstest <MyPublishedTests>.dll --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 Update 5 i nowszych zostanie automatycznie wykryta pożądana struktura.

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostkowe za pomocą testu dotnet i xUnit](unit-testing-with-dotnet-test.md)
- [Testowanie jednostkowe za pomocą testu dotnet i NUnit](unit-testing-with-nunit.md)
- [Testowanie jednostkowe za pomocą testu dotnet i MSTest](unit-testing-with-mstest.md)
