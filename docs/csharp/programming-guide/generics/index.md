---
title: Generics - Przewodnik programowania Języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: c7252180c9c98a8ca99c8cc6b3faaf8b1b8f0749
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167495"
---
# <a name="generics-c-programming-guide"></a>Typy ogólne (Przewodnik programowania w języku C#)

Rodzajowe wprowadzić pojęcie parametrów typu do .NET Framework, które umożliwiają projektowanie klas i metod, które odroczyć specyfikację jednego lub więcej typów, dopóki klasa lub metoda jest zadeklarowana i tworzone przez kod klienta. Na przykład za pomocą parametru `T`typu ogólnego, można napisać jedną klasę, której można użyć inny kod klienta bez ponoszenia kosztów lub ryzyka rzutowania w czasie wykonywania lub operacji bokserskich, jak pokazano poniżej:

[!code-csharp[csProgGuideGenerics#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#1)]

Ogólne klasy i metody łączą możliwości ponownego użycia, bezpieczeństwo typów i wydajność w sposób, który nie może być ich odpowiednikami nierodzajowymi. Rodzajowe są najczęściej używane z kolekcji i metod, które działają na nich. Obszar <xref:System.Collections.Generic> nazw zawiera kilka klas kolekcji ogólnej. Kolekcje nierodzajowe, <xref:System.Collections.ArrayList> takie jak nie są zalecane i są obsługiwane do celów zgodności. Aby uzyskać więcej informacji, zobacz [Generykwi w .NET](../../../standard/generics/index.md).

Oczywiście można również utworzyć niestandardowe typy ogólne i metody, aby zapewnić własne uogólnione rozwiązania i wzorce projektowe, które są bezpieczne dla typu i wydajne. W poniższym przykładzie kodu przedstawiono prostą klasę ogólnej listy połączonej do celów demonstracyjnych. (W większości przypadków należy <xref:System.Collections.Generic.List%601> użyć klasy dostarczonej przez bibliotekę klas .NET Framework zamiast tworzyć własne). Parametr `T` type jest używany w kilku lokalizacjach, w których typ betonu zwykle używany do wskazania typu elementu przechowywanego na liście. Jest on używany w następujący sposób:

- Jako typ parametru metody `AddHead` w metodzie.
- Jako typ zwracany `Data` właściwości w `Node` klasie zagnieżdżonej.
- Jako typ członka prywatnego `data` w klasie zagnieżdżonej.

 Należy `T` zauważyć, że jest `Node` dostępna dla klasy zagnieżdżonej. Gdy `GenericList<T>` jest tworzony z rodzaju betonu, `GenericList<int>`na przykład `T` jako , `int`każde wystąpienie zostanie zastąpione .

[!code-csharp[csProgGuideGenerics#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#2)]

W poniższym przykładzie kodu pokazano, jak kod klienta używa klasy ogólnej `GenericList<T>` do tworzenia listy liczb całkowitych. Po prostu zmieniając argument typu, następujący kod można łatwo zmodyfikować, aby utworzyć listy ciągów lub innego typu niestandardowego:

[!code-csharp[csProgGuideGenerics#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideGenerics/CS/Generics.cs#3)]

## <a name="generics-overview"></a>Ogólny przegląd

- Użyj typów ogólnych, aby zmaksymalizować ponowne użycie kodu, bezpieczeństwo typów i wydajność.
- Najczęstszym zastosowaniem typów ogólnych jest tworzenie klas kolekcji.
- Biblioteka klas .NET Framework zawiera kilka nowych <xref:System.Collections.Generic> klas kolekcji rodzajowych w obszarze nazw. Powinny one być używane, gdy jest <xref:System.Collections.ArrayList> to <xref:System.Collections> możliwe, zamiast klas, takich jak w przestrzeni nazw.
- Można utworzyć własne interfejsy ogólne, klasy, metody, zdarzenia i delegatów.
- Klasy ogólne mogą być ograniczone, aby umożliwić dostęp do metod dla określonych typów danych.
- Informacje o typach, które są używane w typie danych ogólnych można uzyskać w czasie wykonywania przy użyciu odbicia.

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
- [Przewodnik programowania języka C#](../index.md)
- [Typy](../types/index.md)
- [\<>typuparam](../xmldoc/typeparam.md)
- [\<typparamref>](../xmldoc/typeparamref.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
