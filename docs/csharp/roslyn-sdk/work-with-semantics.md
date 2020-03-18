---
title: Praca z modelem semantycznym platformy SDK kompilatora .NET
description: Ten przegląd zawiera zrozumienie typu używanego do zrozumienia i manipulowania modelem semantycznym kodu.
ms.date: 10/15/2017
ms.custom: mvc
ms.openlocfilehash: 8575988cd98a4c0ba3f24107788f065f7472f55d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79156938"
---
# <a name="work-with-semantics"></a>Korzystanie z semantyki

[Drzewa składni](work-with-syntax.md) reprezentują leksykalne i składniowe struktury kodu źródłowego. Mimo że tylko te informacje są wystarczające do opisania wszystkich deklaracji i logiki w źródle, nie jest wystarczająco dużo informacji, aby zidentyfikować, co jest przywoływany. Nazwa może reprezentować:

- typ
- pole
- metoda 
- zmienna lokalna

Chociaż każdy z nich jest unikatowo różny, określenie, do którego identyfikatora faktycznie się odnosi, często wymaga głębokiego zrozumienia reguł językowych.

Istnieją elementy programu reprezentowane w kodzie źródłowym, a programy mogą również odwoływać się do wcześniej skompilowanych bibliotek, spakowanych w plikach zestawu. Mimo że żaden kod źródłowy, a zatem nie ma węzłów składni lub drzew, są dostępne dla zestawów, programy nadal można odwoływać się do elementów wewnątrz nich.

Do tych zadań potrzebny jest **model semantyczny.**

Oprócz modelu składniowego kodu źródłowego model semantyczny hermetyzuje reguły języka, co zapewnia łatwy sposób prawidłowego dopasowania identyfikatorów do odpowiedniego elementu programu, do którego odwołuje się odwołanie.

## <a name="compilation"></a>Kompilacja

Kompilacja jest reprezentacją wszystkiego, co jest potrzebne do skompilowania programu C# lub Visual Basic, który zawiera wszystkie odwołania do zestawu, opcje kompilatora i pliki źródłowe.

Ponieważ wszystkie te informacje znajdują się w jednym miejscu, elementy zawarte w kodzie źródłowym można opisać bardziej szczegółowo. Kompilacja reprezentuje każdy zadeklarowany typ, element członkowski lub zmienną jako symbol. Kompilacja zawiera wiele metod, które pomagają znaleźć i powiązać symbole, które zostały zadeklarowane w kodzie źródłowym lub importowane jako metadane z zestawu.

Podobnie jak drzewa składni, kompilacje są niezmienne. Po utworzeniu kompilacji nie można jej zmienić ani przez Ciebie, ani przez kogokolwiek innego, komu możesz ją udostępnić. Można jednak utworzyć nową kompilację z istniejącej kompilacji, określając zmianę w ten sposób. Na przykład można utworzyć kompilację, która jest taka sama pod każdym względem jak istniejąca kompilacja, z wyjątkiem może zawierać dodatkowy plik źródłowy lub odwołanie do zestawu.

## <a name="symbols"></a>Symbole

Symbol reprezentuje odrębny element zadeklarowany przez kod źródłowy lub importowany z zestawu jako metadane. Każdy obszar nazw, typ, metoda, właściwość, pole, zdarzenie, parametr lub zmienna lokalna jest reprezentowana przez symbol.

Różne metody i właściwości typu <xref:Microsoft.CodeAnalysis.Compilation> ułatwiają znajdowanie symboli. Na przykład można znaleźć symbol zadeklarowanego typu według jego wspólnej nazwy metadanych. Można również uzyskać dostęp do całej tabeli symboli jako drzewa symboli zakorzenionych w globalnej przestrzeni nazw.

Symbole zawierają również dodatkowe informacje, które kompilator określa ze źródła lub metadanych, takich jak inne symbole, do których istnieją odwołania. Każdy rodzaj symbolu jest reprezentowany przez oddzielny <xref:Microsoft.CodeAnalysis.ISymbol>interfejs pochodzący z , każdy z własnymi metodami i właściwościami szczegółowo informacji zebranych przez kompilator. Wiele z tych właściwości bezpośrednio odwoływać się do innych symboli. Na przykład <xref:Microsoft.CodeAnalysis.IMethodSymbol.ReturnType?displayProperty=nameWithType> właściwość informuje o symbolu rzeczywistego typu, do którego odwołuje się deklaracja metody.

Symbole przedstawiają wspólną reprezentację przestrzeni nazw, typów i elementów członkowskich między kodem źródłowym a metadanymi. Na przykład metoda, która została zadeklarowana w kodzie źródłowym i metoda, <xref:Microsoft.CodeAnalysis.IMethodSymbol> która została zaimportowana z metadanych są reprezentowane przez o tych samych właściwościach.

Symbole są podobne w koncepcji do systemu typu <xref:System.Reflection> CLR reprezentowane przez interfejs API, ale są bogatsze w tym, że modelują więcej niż tylko typy. Przestrzenie nazw, zmienne lokalne i etykiety są symbolami. Ponadto symbole są reprezentacją pojęć językowych, a nie pojęć CLR. Istnieje wiele nakładania się, ale istnieje wiele znaczących różnic, jak również. Na przykład metoda iteratora w języku C# lub Visual Basic jest pojedynczym symbolem. Jednak gdy metoda iteratora jest tłumaczona na metadane CLR, jest typem i wieloma metodami.

## <a name="semantic-model"></a>Model semantyczny

Model semantyczny reprezentuje wszystkie informacje semantyczne dla pojedynczego pliku źródłowego. Można go użyć, aby odkryć następujące elementy:

- Symbole, do których odwołuje się w określonej lokalizacji w źródle.
- Wynikowy typ dowolnego wyrażenia.
- Wszystkie diagnostyki, które są błędy i ostrzeżenia.
- Jak zmienne przepływają do i z regionów źródła.
- Odpowiedzi na pytania bardziej spekulacyjne.
