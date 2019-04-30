---
title: Praca z zestawu SDK platformy kompilatora .NET semantycznego modelu analizy biznesowej
description: Ten przegląd zawiera opis typów, używaną do manipulowania semantycznego modelu kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: cf34e2ab9688325f58cb54755db4142a883fca77
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706640"
---
# <a name="work-with-semantics"></a>Korzystanie z semantyki

[Drzewa składni](work-with-syntax.md) reprezentują leksykalne i składniowych struktury kodu źródłowego. Mimo że te informacje tylko jest wystarczająca do opisywania, deklaracje i logiki w źródle, nie jest wystarczająco dużo informacji do identyfikacji, co jest ono przywoływane. Nazwa może reprezentować:

- Typ
- Pola
- Metoda
- Zmienna lokalna

Mimo że każdy z nich jest jednoznacznie inny, określania, który z nich odpowiadającym faktycznie odnosi się do często wymaga głębokiego zrozumienie reguły języka. 

Istnieją elementy programu reprezentowane w kodzie źródłowym i programów znajdują się wcześniej skompilowanych bibliotek, spakowane w zestawie plików. Brak kodu źródłowego i w związku z tym żadnych węzłów składni lub drzewa, są dostępne dla zestawów, programy nadal mogą odwoływać się do elementów wewnątrz nich.

W przypadku tych zadań należy **semantycznego modelu analizy biznesowej**.

Oprócz modelu składni kodu źródłowego modelu semantycznego hermetyzuje reguły języka, co zapewnia łatwy sposób poprawnie zgodne identyfikatory z elementem odpowiedniego programu, do którego nastąpiło odwołanie.

## <a name="compilation"></a>Kompilacja

Kompilacja jest reprezentacją wszystko, co jest potrzebne do kompilowania C# program lub Visual Basic, który zawiera wszystkie odwołania do zestawów, opcje kompilatora i plików źródłowych. 

Ponieważ te informacje w jednym miejscu, elementy zawarte w kodzie źródłowym można opisane bardziej szczegółowo. Kompilacja reprezentuje każdego deklarowanego typu, elementu członkowskiego lub zmiennej jako symbol separatora. Kompilacja zawiera szereg metod, które ułatwiają znajdowanie i odnoszą się symboli, które mają została zadeklarowana w kodzie źródłowym lub importowany jako metadane z zestawu.

Podobnie jak drzewa składni, kompilacje są niezmienne. Po utworzeniu kompilacji, nie można zmienić przez nikogo, który może być używany z. Jednak można utworzyć nowej kompilacji z istniejącej kompilacji, określając zmiany, jak można to zrobić. Na przykład może utworzyć kompilacji, która jest taka sama w sposób, co jako istniejące kompilacji, z wyjątkiem może zawierać dodatkowe pliku lub zestawu odwołania do źródła.

## <a name="symbols"></a>Symbole

Symbol reprezentuje element distinct zadeklarowane na podstawie kodu źródłowego lub importowane z zestawu jako metadane. Co przestrzeni nazw, typu, metody, właściwości, pola, zdarzenia, parametr lub zmienna lokalna jest reprezentowany przez symbol. 

Różne metody i właściwości <xref:Microsoft.CodeAnalysis.Compilation> wpisz pomóc w znalezieniu symboli. Na przykład można znaleźć symbolu dla zadeklarowanym typem według nazwy pospolitej metadanych. Można również uzyskać dostęp tabeli symboli całego jako drzewo symboli umieszczone w globalnej przestrzeni nazw.

Symbole również zawierać dodatkowe informacje, które kompilator określa ze źródła lub metadane, takie jak inne odwołania symboli. Każdy rodzaj symbolu jest reprezentowany przez oddzielny interfejs pochodną <xref:Microsoft.CodeAnalysis.ISymbol>, każda z metod i właściwości ze szczegółami dotyczącymi informacje zebrane przez kompilator. Wiele z tych właściwości bezpośrednio odwoływać innych symboli. Na przykład <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> właściwość zawiera informacje, symbol rzeczywisty typ, który odwołuje się do deklaracji metody.

Symbole przedstawiają reprezentację wspólnej przestrzeni nazw, typów i członków, między kodem źródłowym i metadanych. Na przykład, metody, która została zadeklarowana w kodzie źródłowym i metody, które zostały zaimportowane z metadanych są zarówno reprezentowane przez <xref:Microsoft.CodeAnalysis.IMethodSymbol> z tymi samymi właściwościami.

Symbole są podobne do systemu typów CLR reprezentowany przez <xref:System.Reflection> interfejsu API, ale one są bardziej rozbudowane, modelują one więcej niż tylko typy. Przestrzenie nazw, zmienne lokalne i etykiety są wszystkie symbole. Ponadto symbole są reprezentacją koncepcje językowe i nie pojęcia dotyczące środowiska CLR. Jest dużo nakładają się na siebie, ale istnieje wiele również istotne różnice. Na przykład metoda iteratora jest w C# lub Visual Basic to pojedynczy symbol. Jednakże gdy metoda iteratora jest tłumaczona na metadanych CLR, jest typem i na wiele sposobów.

## <a name="semantic-model"></a>Semantyczny model analizy biznesowej

Model semantyczny reprezentuje wszystkie informacje semantyczne jednym pliku źródłowym. Służy do odnajdywania następujące czynności: 

* Symbole, do których odwołuje się w określonym miejscu w źródle.
* Wynikowy typ dowolne wyrażenie.
* Testy diagnostyczne, które są błędy i ostrzeżenia.
* Jak zmienne przenoszone do regionów źródłowych.
* Odpowiedzi na pytania bardziej spekulacyjnego.
