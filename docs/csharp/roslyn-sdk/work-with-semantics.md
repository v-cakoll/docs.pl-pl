---
title: Praca z zestawu SDK platformy kompilatora .NET semantycznego modelu
description: "Ten przegląd zawiera opis typu, który służy do zrozumienia i manipulowania semantycznego modelu kodu."
author: billwagner
ms.author: wiwagn
ms.date: 10/15/2017
ms.topic: conceptual
ms.prod: .net
ms.devlang: devlang-csharp
ms.custom: mvc
ms.openlocfilehash: 28366093c516f5367d82c0bdfc53749e764361ef
ms.sourcegitcommit: d095094e942eedf09530ea5636fbaf9029853027
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2017
---
# <a name="work-with-semantics"></a>Praca z semantyki

[Drzewa składni](work-with-syntax.md) reprezentują leksykalne i składni struktury kodu źródłowego. Tych samych informacji jest wystarczająca do opisywania wszystkie deklaracje i logiki w źródle, ale nie jest on wystarczających informacji do identyfikowania co odwołuje się do. Nazwa może reprezentować:

- Typ
- Pola
- — Metoda
- Zmienna lokalna

Mimo że każda z tych jednoznacznie różnych, określania, który faktycznie odwołuje się identyfikator często wymaga dokładnego zrozumienia reguł języka. 

Istnieją elementy programu reprezentowane w kodzie źródłowym i programów znajdują się wcześniej skompilowanej biblioteki, umieszczone w zestawie plików. Brak kodu źródłowego i w związku z tym żadnych węzłów składni lub drzewa, są dostępne dla zestawów, programy nadal mogą odwoływać się do elementów zawartych w nich.

Dla tych zadań należy **modelu semantycznego**.

Oprócz składni modelu kodu źródłowego modelu semantycznego hermetyzuje reguł języka, umożliwiając łatwe pasuje identyfikatory z elementem odpowiedniego programu, do którego nastąpiło odwołanie.

## <a name="compilation"></a>Kompilacja

Kompilacja jest reprezentacja wszystko, co jest potrzebne do kompilacji C# lub Visual Basic program, który zawiera wszystkie odwołania do zestawów, opcje kompilatora i plików źródłowych. 

Ponieważ te informacje w jednym miejscu, elementy zawarte w kodzie źródłowym można opisane bardziej szczegółowo. Kompilacja reprezentuje każdego deklarowanego typu, elementu członkowskiego lub zmiennej jako symbolu. Kompilacja zawiera różnych metod, które ułatwiają znajdowanie i dotyczą symbole, które mają został zadeklarowany w kodzie źródłowym albo zaimportowana jako metadanych z zestawu.

Podobnie jak drzewa składni, kompilacje są niezmienne. Po utworzeniu kompilacji nie można zmienić przez Ciebie ani przez żadną inną osobę, który może być używany z. Jednak można utworzyć nowej kompilacji z istniejących kompilacji Określanie zmiany, jak możesz to zrobić. Na przykład utworzyć kompilacji, jest taka sama w sposób, co jako istniejących kompilacji, z wyjątkiem może zawierać dodatkowe pliku lub zestawu odwołanie do źródła.

## <a name="symbols"></a>Symbole

Symbol reprezentuje element distinct zgłoszone przez kod źródłowy lub zaimportowane z zestawu metadanych. Co przestrzeni nazw, typu, — metoda, właściwość, pola, zdarzenia, parametr lub zmienna lokalna jest reprezentowany przez symbol. 

Różnych metod i właściwości na <xref:Microsoft.CodeAnalysis.Compilation> wpisz pomóc w znalezieniu symboli. Na przykład można znaleźć symbolu dla deklarowanego typu według nazwy pospolitej metadanych. Można także przejść tabeli symboli całego jako drzewo symboli umieszczone w globalnej przestrzeni nazw.

Symbole również zawierać dodatkowe informacje, które określa kompilator ze źródła lub metadane, takie jak innych przywoływanego symboli. Każdego rodzaju symbolu jest reprezentowana przez oddzielny interfejs pochodny <xref:Microsoft.CodeAnalysis.ISymbol>, każdej z metod i właściwości opisujące informacje zebrane przez kompilator. Wiele z tych właściwości bezpośrednio odwoływać się inne symbole. Na przykład <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> właściwości informuje symbol rzeczywisty typ, który odwołuje się do deklaracji metody.

Symbole stanowi reprezentację wspólnej przestrzeni nazw, typów i członków między kodu źródłowego i metadanych. Na przykład metodę, która została zadeklarowana w kodzie źródłowym i metody, które zostały zaimportowane z metadanych są oba reprezentowane przez <xref:Microsoft.CodeAnalysis.IMethodSymbol> z tej samej właściwości.

Symbole są podobne do system typów CLR reprezentowany przez <xref:System.Reflection> interfejsu API, ale ich są bardziej rozbudowane, w tym modelu są tylko typy. Przestrzenie nazw, zmienne lokalne i etykiety są wszystkie symbole. Ponadto symbole są reprezentację pojęcia dotyczące języka, nie pojęcia dotyczące środowiska CLR. Wiele nakładają się na siebie, ale istnieją także wiele rozróżnienia łatwy do rozpoznania. Na przykład metodę iteratora w języku C# lub Visual Basic jest jeden symbol. Jednak podczas translacji metodę iteratora metadanych CLR jest typem i wiele metod.

## <a name="semantic-model"></a>Model semantyczny analizy biznesowej

Modelu semantycznego reprezentuje wszystkie informacje semantyczne jednym pliku źródłowym. Umożliwia odnajdywania następujące czynności: 

* Symbole odwołuje się do określonych lokalizacji w źródle.
* Wynikowy typ dowolne wyrażenie.
* Diagnostyka wszystkie, które są błędy i ostrzeżenia.
* Jak zmienne przepływu i regiony źródła.
* Odpowiedzi na pytania więcej rozważana.
