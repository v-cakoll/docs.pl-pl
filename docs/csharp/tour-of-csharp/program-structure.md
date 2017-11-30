---
title: "C# Program struktury — samouczek języka C#"
description: "Dowiedz się, podstawowe bloki konstrukcyjne program C#"
keywords: Oprogramowanie .NET core .NET
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 8d8f443f8458cd392c75e9787e612ca1cc3518c7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="program-structure"></a>Struktura programu

Podstawowe pojęcia organizacji w języku C# to ***programy***, ***przestrzeni nazw***, ***typy***, ***członków***, i ***zestawy***. C# programy składają się z co najmniej jeden plik źródłowy. Programy deklaruj typy, które zawierają elementy członkowskie i można organizować w przestrzeni nazw. Klasy i interfejsy są przykłady typów. Pola, metody, właściwości i zdarzenia są przykłady elementów członkowskich. Gdy są kompilowane programów C#, są one fizycznie umieszczone w zestawy. Zestawy zwykle mają rozszerzenia pliku `.exe` lub `.dll`w zależności od tego, czy wdrożenie ***aplikacji*** lub ***biblioteki***odpowiednio.

Przykład deklaruje klasę o nazwie `Stack` w obszarze nazw o nazwie `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowana nazwa ta klasa jest `Acme.Collections.Stack`. Klasa zawiera kilka elementów członkowskich: pola o nazwie `top`, dwie metody o nazwie `Push` i `Pop`i zagnieżdżone klasy o nazwie `Entry`. `Entry` Dalsze klasa zawiera trzy elementy członkowskie: pola o nazwie `next`, pole o nazwie `data`ani konstruktora. Przy założeniu, że kod źródłowy przykładu znajduje się w pliku `acme.cs`, wiersza polecenia

```
csc /t:library acme.cs
```

kompiluje przykład jako biblioteki (code bez `Main` punktu wejścia) i tworzy zestaw o nazwie `acme.dll`.

> [!IMPORTANT]
> Przykłady powyżej użyj `csc` jako kompilatora wiersza polecenia języka C#. Ten kompilator jest wykonywalne systemu windows. Aby użyć C# na innych platformach, należy używać narzędzi dla platformy .NET Core. Używa ekosystemu platformy .NET Core `dotnet` interfejsu wiersza polecenia do zarządzania kompilacji wiersza polecenia. W tym zarządzanie zależności i wywoływanie kompilatora C#. Zobacz [w tym samouczku](../../core/tutorials/using-with-xplat-cli.md) pełen opis tych narzędzi na platformach obsługiwanych przez oprogramowanie .NET Core.

Zestaw nie zawiera kodu wykonywalnego w postaci instrukcji w języku pośrednim (IL) i symboliczne informacje w postaci metadanych. Przed wykonaniem jego kod IL w zestawie jest automatycznie konwertowany do specyficznych dla procesora kodu za pomocą kompilatora just in Time (JIT) aparatu plików wykonywalnych języka wspólnego .NET.

Ponieważ zestaw jest samoopisujące jednostka zawierająca kod i metadanych funkcji, nie jest wymagane dla `#include` dyrektywy i pliki nagłówkowe w języku C#. Typy publiczne i elementów członkowskich zawartych w określonym zestawie stają się dostępne w programie C# za pomocą odwołania do tego zestawu, w przypadku kompilowania kodu programu. Na przykład ten program używa `Acme.Collections.Stack` klasę z `acme.dll` zestawu:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Jeśli program jest przechowywany w pliku `example.cs`, gdy `example.cs` jest skompilowany, zestawu acme.dll można odwoływać się przy użyciu /r — opcja kompilatora:

```
csc /r:acme.dll example.cs
```

Spowoduje to utworzenie pliku wykonywalnego zestawu o nazwie `example.exe`, która po uruchomieniu tworzy dane wyjściowe:

```
100
10
1
```

C# zezwala na tekst źródłowy program ma być przechowywana w kilka plików źródłowych. Podczas kompilowania wielu plików programu C#, są ze sobą przetwarzanie wszystkich plików źródłowych i plików źródłowych za darmo można odwoływać się siebie nawzajem — koncepcyjnie, są tak, jakby wszystkie pliki źródłowe zostały połączone w jeden plik dużych przed przetworzeniem. Deklaracje do przodu nigdy nie są potrzebne w języku C#, ponieważ z nielicznymi wyjątkami kolejności deklaracji jest niewielka. C# nie istnieje limit pliku źródłowego do deklarowania tylko jeden typ publiczny, ani nie wymaga nazwy pliku źródłowego, aby dopasować typ zadeklarowany w pliku źródłowym.

>[!div class="step-by-step"]
[Poprzednie](index.md)
[dalej](types-and-variables.md)
