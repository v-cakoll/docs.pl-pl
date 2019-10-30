---
title: Typy ogólne — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 4ff0dd872e1b09e993c947f008c964ad204ad09a
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039357"
---
# <a name="generics-c-programming-guide"></a>Typy ogólne (Przewodnik programowania w języku C#)

Typy ogólne wprowadzają koncepcję parametrów typu do .NET Framework, co umożliwia zaprojektowanie klas i metod, które opóźniają specyfikację jednego lub kilku typów do momentu zadeklarowania klasy lub metody i wystąpienia przez kod klienta. Na przykład przy użyciu parametru typu ogólnego `T`można napisać pojedynczą klasę, której może użyć inny kod klienta, bez ponoszenia kosztów lub ryzyka związanego z rzutowaniem lub zapakowywaniem środowiska uruchomieniowego, jak pokazano poniżej:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Klasy generyczne i metody łączą użyteczność, bezpieczeństwo typów i wydajność w taki sposób, że ich nieogólnymi odpowiednikami nie jest. Typy ogólne są najczęściej używane z kolekcjami i metodami, które działają na nich. Przestrzeń nazw <xref:System.Collections.Generic> zawiera kilka ogólnych klas kolekcji. Kolekcje inne niż ogólne, takie jak <xref:System.Collections.ArrayList> nie są zalecane i są obsługiwane w celu zapewnienia zgodności. Aby uzyskać więcej informacji, zobacz [typy ogólne w programie .NET](../../../standard/generics/index.md).

Oczywiście można również tworzyć niestandardowe typy ogólne i metody w celu udostępniania własnych uogólnionych rozwiązań i wzorców projektowych, które są bezpieczne i wydajne. Poniższy przykład kodu pokazuje prostą ogólną klasę listy połączonej w celach demonstracyjnych. (W większości przypadków należy użyć klasy <xref:System.Collections.Generic.List%601> dostarczonej przez bibliotekę klas .NET Framework zamiast tworzyć własne). Parametr typu `T` jest używany w kilku lokalizacjach, w których konkretny typ jest zwykle używany do wskazania typu elementu przechowywanego na liście. Jest on używany w następujący sposób:

- Jako typ parametru metody w metodzie `AddHead`.
- Jako zwracany typ właściwości `Data` w klasie `Node` zagnieżdżonych.
- Jako typ prywatnego elementu członkowskiego `data` w klasie zagnieżdżonej.

 Należy pamiętać, że `T` jest dostępny dla zagnieżdżonej klasy `Node`. Gdy `GenericList<T>` jest tworzone przy użyciu konkretnego typu, na przykład jako `GenericList<int>`, każde wystąpienie `T` zostanie zastąpione `int`.

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)] 

Poniższy przykład kodu pokazuje, jak kod klienta używa klasy generycznej `GenericList<T>` do tworzenia listy liczb całkowitych. Po prostu poprzez zmianę argumentu typu można łatwo zmodyfikować następujący kod w celu utworzenia list ciągów lub dowolnego innego typu niestandardowego:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Ogólne — przegląd

- Używaj typów ogólnych do maksymalizowania ponownego użycia kodu, bezpieczeństwa typów i wydajności.
- Typowym zastosowaniem typów ogólnych jest utworzenie klas kolekcji.
- Biblioteka klas .NET Framework zawiera kilka nowych klas kolekcji ogólnych w przestrzeni nazw <xref:System.Collections.Generic>. Powinny one być używane, gdy jest to możliwe, zamiast klas takich jak <xref:System.Collections.ArrayList> w przestrzeni nazw <xref:System.Collections>.
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
- [Typy ogólne w czasie wykonywania](generics-in-the-run-time.md)

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).

## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Generic>
- [Przewodnik programowania w języku C#](../index.md)
- [Typy](../types/index.md)
- [\<typeparam >](../xmldoc/typeparam.md)
- [\<typeparamref >](../xmldoc/typeparamref.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
