---
title: C#Program, struktura — Przewodnik po przykładzie C# języka
description: Dowiedz się, podstawowe bloki konstrukcyjne C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: de10cd000b4028a66ce6dd6f21e39c013e38ecd2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61675952"
---
# <a name="program-structure"></a>Struktura programu

Kluczowe założenia organizacji w języku C# są ***programy***, ***przestrzenie nazw***, ***typy***, ***członków***, i ***zestawy***. C# programy składają się z jednego lub więcej plików źródłowych. Programy deklarują typy, które zawierają elementy członkowskie i mogą być organizowane w przestrzeni nazw. Klasy i interfejsy są przykłady typów. Pola, metody, właściwości i zdarzenia są przykłady elementów członkowskich. Po skompilowaniu C# programy są fizycznie spakowane do zestawów. Zestawy zwykle z rozszerzeniem pliku `.exe` lub `.dll`, w zależności od tego, czy zaimplementować ***aplikacje*** lub ***biblioteki***, odpowiednio.

Przykład deklaruje klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowana nazwa tej klasy to `Acme.Collections.Stack`. Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop`i klasę zagnieżdżoną o nazwie `Entry`. `Entry` Dodatkowo klasa zawiera trzy elementy członkowskie: pole o nazwie `next`, pole o nazwie `data`i konstruktora. Przy założeniu, że kod źródłowy przykładu znajduje się w pliku `acme.cs`, wiersza polecenia

```
csc /t:library acme.cs
```

kompiluje przykład jako biblioteki (kod bez `Main` punktu wejścia) i tworzy zestaw o nazwie `acme.dll`.

> [!IMPORTANT]
> Przykłady powyżej użyj `csc` wiersz polecenia C# kompilatora. Tym kompilatorze jest plikiem wykonywalnym Windows. Aby użyć C# na innych platformach, należy używać narzędzi dla platformy .NET Core. Ekosystem platformy .NET Core używa `dotnet` interfejsu wiersza polecenia do zarządzania kompilacji z wiersza polecenia. Obejmuje to zarządzanie zależnościami i wywoływanie C# kompilatora. Zobacz [w tym samouczku](../../core/tutorials/using-with-xplat-cli.md) pełny opis tych narzędzi na platformach obsługiwanych przez platformy .NET Core.

Zestawy zawierają kodu wykonywalnego w formie instrukcje języka pośredniego (IL) i informacji o symbolach w postaci metadanych. Przed wykonaniem jego kodu IL w zestawie jest automatycznie konwertowany na kod specyficzny dla procesora przez kompilator just in Time (JIT) środowiska uruchomieniowego języka wspólnego platformy .NET.

Ponieważ zestaw jest samoopisujący jednostka zawierająca kod i metadanych funkcji, nie ma potrzeby dla `#include` dyrektyw i pliki nagłówkowe w języku C#. Typy publiczne i elementów członkowskich znajdujących się w określonym zestawie są udostępniane w programie C# poprzez odwołanie do tego zestawu podczas kompilowania kodu programu. Na przykład ten program używa `Acme.Collections.Stack` klasy z `acme.dll` zestawu:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Jeśli program jest przechowywany w pliku `example.cs`, gdy `example.cs` jest kompilowany, zestawu acme.dll można odwoływać się za pomocą /r — opcja kompilatora:

```
csc /r:acme.dll example.cs
```

Spowoduje to utworzenie pliku wykonywalnego zestaw o nazwie `example.exe`, który, po uruchomieniu tworzy dane wyjściowe:

```
100
10
1
```

C# umożliwia tekst źródłowy program ma być przechowywany w kilku plików źródłowych. Wielu plików języka C# program jest skompilowany, wszystkie pliki źródłowe są przetwarzane razem, gdy pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — model jest tak, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem. Deklaracje przechodzenia do przodu nigdy nie są wymagane w języku C#, ponieważ z nielicznymi wyjątkami, kolejności deklaracji jest niewielka. C# nie istnieje limit pliku źródłowego do deklarowania tylko jeden typ publiczny ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.

>[!div class="step-by-step"]
>[Poprzednie](index.md)
>[dalej](types-and-variables.md)