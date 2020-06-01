---
title: Typy ogólne — Przewodnik programowania w języku C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: a3ed3aa412c7d9c9d6b705dba80b527057c647fa
ms.sourcegitcommit: a241301495a84cc8c64fe972330d16edd619868b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/01/2020
ms.locfileid: "84241672"
---
# <a name="generics-c-programming-guide"></a>Typy ogólne (Przewodnik programowania w języku C#)

Typy ogólne wprowadzają koncepcję parametrów typu do platformy .NET, co pozwala na projektowanie klas i metod, które opóźniają specyfikację jednego lub więcej typów do momentu zadeklarowania klasy lub metody jako wystąpienia przez kod klienta. Na przykład przy użyciu parametru typu ogólnego można `T` napisać pojedynczą klasę, która może być używana przez inny kod klienta bez ponoszenia kosztów lub ryzyka rzutowania w czasie wykonywania lub operacji pakowania, jak pokazano poniżej:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Klasy generyczne i metody łączą użyteczność, bezpieczeństwo typów i wydajność w taki sposób, że ich nieogólnymi odpowiednikami nie jest. Typy ogólne są najczęściej używane z kolekcjami i metodami, które działają na nich. <xref:System.Collections.Generic>Przestrzeń nazw zawiera kilka rodzajowych klas kolekcji. Kolekcje inne niż ogólne, takie jak <xref:System.Collections.ArrayList> nie są zalecane i są obsługiwane w celu zapewnienia zgodności. Aby uzyskać więcej informacji, zobacz [typy ogólne w programie .NET](../../../standard/generics/index.md).

Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu udostępniania własnych uogólnionych rozwiązań i wzorców projektowych, które są bezpieczne i wydajne. Poniższy przykład kodu pokazuje prostą ogólną klasę listy połączonej w celach demonstracyjnych. (W większości przypadków należy użyć <xref:System.Collections.Generic.List%601> klasy dostarczonej przez platformę .NET zamiast tworzenia własnych). Parametr typu `T` jest używany w kilku lokalizacjach, w których konkretny typ jest zwykle używany do wskazania typu elementu przechowywanego na liście. Jest on używany w następujący sposób:

- Jako typ parametru metody w `AddHead` metodzie.
- Jako zwracany typ `Data` właściwości w klasie zagnieżdżonej `Node` .
- Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.

 Należy pamiętać, że `T` jest ona dostępna dla klasy zagnieżdżonej `Node` . Gdy `GenericList<T>` jest tworzona przy użyciu konkretnego typu, na przykład jako `GenericList<int>` , każde wystąpienie `T` zostanie zastąpione `int` .

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

Poniższy przykład kodu pokazuje, jak kod klienta używa klasy generycznej `GenericList<T>` do tworzenia listy liczb całkowitych. Po prostu poprzez zmianę argumentu typu można łatwo zmodyfikować następujący kod w celu utworzenia list ciągów lub dowolnego innego typu niestandardowego:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Ogólne — przegląd

- Używaj typów ogólnych do maksymalizowania ponownego użycia kodu, bezpieczeństwa typów i wydajności.
- Typowym zastosowaniem typów ogólnych jest utworzenie klas kolekcji.
- Biblioteka klas .NET zawiera kilka ogólnych klas kolekcji w <xref:System.Collections.Generic> przestrzeni nazw. Powinny one być używane w miarę możliwości zamiast klas takich jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.
- Można tworzyć własne interfejsy, klasy, metody, zdarzenia i Delegaty.
- Klasy generyczne mogą być ograniczone, aby umożliwić dostęp do metod dla konkretnych typów danych.
- Informacje na temat typów, które są używane w ogólnym typie danych, można uzyskać w czasie wykonywania przy użyciu odbicia.

## <a name="related-sections"></a>Sekcje pokrewne

- [Parametry typu ogólnego](generic-type-parameters.md)
- [Ograniczenia dotyczące parametrów typu](constraints-on-type-parameters.md)
- [Klasy ogólne](generic-classes.md)
- [Interfejsy ogólne](generic-interfaces.md)
- [Metody ogólne](generic-methods.md)
- [Delegaci ogólni](generic-delegates.md)
- [Różnice między szablonami C++ i typami ogólnymi C#](differences-between-cpp-templates-and-csharp-generics.md)
- [Typy ogólne i odbicie](generics-and-reflection.md)
- [Typy ogólne w środowisku uruchomieniowym](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).

## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy](../types/index.md)
- [\<typeparam>](../xmldoc/typeparam.md)
- [\<typeparamref>](../xmldoc/typeparamref.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
