---
title: Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet
description: Dowiedz się, jak uruchamiać testy w opublikowanych bibliotekach, a nie w kodzie źródłowym, za pomocą polecenia dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 9ac03053bc762d0176e087545871ca8a145cd41e
ms.sourcegitcommit: 1b020356e421a9314dd525539da12463d980ce7a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/30/2019
ms.locfileid: "70168297"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet

Można uruchomić testy dla już opublikowanych danych wyjściowych za pomocą `dotnet vstest` polecenia. Będzie to działało na testach xUnit, MSTest i NUnit. Po prostu zlokalizuj plik DLL, który był częścią opublikowanych danych wyjściowych, i uruchom:

```console
dotnet vstest <MyPublishedTests>.dll
```

Gdzie `<MyPublishedTests>` to nazwa opublikowanego projektu testowego.

## <a name="example"></a>Przykład

Poniższe polecenia przedstawiają uruchamianie testów w opublikowanej bibliotece DLL.

```console
dotnet new mstest -o MyProject.Tests
cd MyProject.Tests
dotnet publish -o out
dotnet vstest out/MyProject.Tests.dll
```

> [!NOTE]
> Uwaga: Jeśli aplikacja jest ukierunkowana na platformę inną `netcoreapp` niż nadal można `dotnet vstest` uruchomić polecenie, przekazując w platformę docelową flagę platformy. Na przykład `dotnet vstest <MyPublishedTests>.dll  --Framework:".NETFramework,Version=v4.6"`. W programie Visual Studio 2017 Update 5 żądana platforma jest wykrywana automatycznie.

## <a name="see-also"></a>Zobacz także

- [Testowanie jednostkowe za pomocą testu dotnet i xUnit](unit-testing-with-dotnet-test.md)
- [Testowanie jednostkowe za pomocą testu dotnet i NUnit](unit-testing-with-nunit.md)
- [Testowanie jednostkowe za pomocą testu dotnet i MSTest](unit-testing-with-mstest.md)
