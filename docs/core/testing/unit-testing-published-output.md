---
title: Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet
description: Dowiedz się, jak uruchamiać testy w opublikowanych bibliotekach, a nie w kodzie źródłowym, za pomocą polecenia dotnet VSTest.
author: kendrahavens
ms.author: kehavens
ms.date: 10/18/2017
ms.custom: seodec18
ms.openlocfilehash: 93b2e1a433b5d5b9694257d4d12e47d9107f4cd7
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117024"
---
# <a name="test-published-output-with-dotnet-vstest"></a>Testowanie opublikowanych danych wyjściowych przy użyciu VSTest dotnet

Można uruchomić testy dla już opublikowanych danych wyjściowych za pomocą `dotnet vstest` polecenia. Będzie to działało na testach xUnit, MSTest i NUnit. Po prostu zlokalizuj plik DLL, który był częścią opublikowanych danych wyjściowych, i uruchom:

```dotnetcli
dotnet vstest <MyPublishedTests>.dll
```

Gdzie `<MyPublishedTests>` to nazwa opublikowanego projektu testowego.

## <a name="example"></a>Przykład

Poniższe polecenia przedstawiają uruchamianie testów w opublikowanej bibliotece DLL.

```dotnetcli
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
