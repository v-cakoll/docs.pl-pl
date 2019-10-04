---
title: C#Struktura programu — Przewodnik po C# języku
description: Zapoznaj się z podstawowymi blokami konstrukcyjnymi C# programu
ms.date: 08/10/2016
ms.assetid: 984f0314-507f-47a0-af56-9011243f5e65
ms.openlocfilehash: 5102c72d68108f698a0456b9c14e6713778f4325
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834156"
---
# <a name="program-structure"></a>Struktura programu

Kluczowe koncepcje organizacyjne C# w programie to ***programy***, ***przestrzenie nazw***, ***typy***, ***elementy członkowskie***i ***zestawy***. C#programy składają się z co najmniej jednego pliku źródłowego. Programy deklarują typy, które zawierają składowe i mogą być zorganizowane w przestrzenie nazw. Klasy i interfejsy są przykładami typów. Pola, metody, właściwości i zdarzenia są przykładami elementów członkowskich. Gdy C# programy są kompilowane, są fizycznie spakowane do zestawów. Zestawy zazwyczaj mają rozszerzenie pliku `.exe` lub `.dll`, w zależności od tego, czy implementują odpowiednio ***aplikacje*** lub ***biblioteki***.

Przykład deklaruje klasę o nazwie `Stack` w przestrzeni nazw o nazwie `Acme.Collections`:

[!code-csharp[Stack](../../../samples/snippets/csharp/tour/program-structure/program.cs#L1-L34)]

W pełni kwalifikowana nazwa tej klasy jest `Acme.Collections.Stack`. Klasa zawiera kilka elementów członkowskich: pole o nazwie `top`, dwie metody o nazwie `Push` i `Pop` oraz zagnieżdżoną klasę o nazwie `Entry`. Klasa `Entry` zawiera więcej trzech elementów członkowskich: pole o nazwie `next`, pole o nazwie `data` i Konstruktor. Przy założeniu, że kod źródłowy przykładu jest przechowywany w pliku `acme.cs`, wiersz polecenia

```console
csc /t:library acme.cs
```

kompiluje przykład jako bibliotekę (kod bez punktu wejścia `Main`) i tworzy zestaw o nazwie `acme.dll`.

> [!IMPORTANT]
> W powyższych przykładach użyto `csc` jako kompilatora wiersza C# polecenia. Ten kompilator jest plikiem wykonywalnym systemu Windows. Aby korzystać C# z różnych platform, należy użyć narzędzi dla platformy .NET Core. Ekosystem platformy .NET Core używa interfejsu wiersza polecenia `dotnet` do zarządzania kompilacjami w wierszu poleceń. Obejmuje to zarządzanie zależnościami i wywoływanie C# kompilatora. Zapoznaj się z [tym samouczkiem](../../core/tutorials/using-with-xplat-cli.md) , aby zapoznać się z pełnymi opisami tych narzędzi na platformach obsługiwanych przez platformę .NET Core.

Zestawy zawierają kod wykonywalny w postaci instrukcji języka pośredniego (IL) i informacji symbolicznych w formie metadanych. Przed wykonaniem kod IL w zestawie jest automatycznie konwertowany na kod specyficzny dla procesora przez kompilator just-in-Time (JIT) środowiska uruchomieniowego języka wspólnego platformy .NET.

Ponieważ zestaw jest samoopisującą się jednostką funkcji, która zawiera kod i metadane, nie ma potrzeby stosowania dyrektyw `#include` i plików nagłówkowych w C#programie. Typy publiczne i składowe zawarte w określonym zestawie są udostępniane w C# programie po prostu przez odwołanie się do tego zestawu podczas kompilowania programu. Na przykład ten program używa klasy `Acme.Collections.Stack` z zestawu `acme.dll`:

[!code-csharp[UsingStack](../../../samples/snippets/csharp/tour/program-structure/Program.cs#L38-L52)]

Jeśli program jest przechowywany w pliku `example.cs`, gdy zostanie skompilowany `example.cs`, można odwoływać się do zestawu Acme. dll przy użyciu opcji/r kompilatora:

```console
csc /r:acme.dll example.cs
```

Spowoduje to utworzenie zestawu wykonywalnego o nazwie `example.exe`, który w przypadku uruchamiania generuje wynik:

```console
100
10
1
```

C#zezwala na przechowywanie tekstu źródłowego programu w kilku plikach źródłowych. W przypadku kompilowania programu C# z obsługą wielu plików wszystkie pliki źródłowe są przetwarzane razem, a pliki źródłowe mogą swobodnie odwoływać się do siebie nawzajem — jest to tak samo, jakby wszystkie pliki źródłowe zostały połączone w jeden duży plik przed przetworzeniem. Deklaracje przesyłania dalej nie są C# nigdy niewymagane w programie, w związku z czym z kilkoma wyjątkami, zamówienie deklaracji jest nieważne. C#nie ogranicza pliku źródłowego do deklarowania tylko jednego typu publicznego ani nie wymaga, aby nazwa pliku źródłowego była zgodna z typem zadeklarowanym w pliku źródłowym.

>[!div class="step-by-step"]
>[Poprzedni](index.md)
>[Następny](types-and-variables.md)
