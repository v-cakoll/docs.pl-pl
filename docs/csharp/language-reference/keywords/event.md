---
title: event - Odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- event
- remove
- event_CSharpKeyword
- add
helpviewer_keywords:
- event keyword [C#]
ms.assetid: 7858fd85-153b-4259-85d0-6aa13c35f174
ms.openlocfilehash: eb1805ed55921497fea88e6b39989c876ef003d1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713554"
---
# <a name="event-c-reference"></a>zdarzenie (odwołanie do języka C#)

Słowo `event` kluczowe służy do deklarowania zdarzenia w klasie wydawcy.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak <xref:System.EventHandler> zadeklarować i podnieść zdarzenie, które używa jako podstawowego typu delegata. W przypadku pełnego przykładu kodu, który <xref:System.EventHandler%601> pokazuje również, jak używać ogólnego typu delegata i jak subskrybować zdarzenie i utworzyć metodę obsługi zdarzeń, zobacz [Jak publikować zdarzenia zgodne z wytycznymi platformy .NET Framework](../../programming-guide/events/how-to-publish-events-that-conform-to-net-framework-guidelines.md).

[!code-csharp[csrefKeywordsModifiers#7](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#7)]

Zdarzenia są specjalny rodzaj delegata multiemisji, które mogą być wywoływane tylko z wewnątrz klasy lub struktury, gdzie są zadeklarowane (klasa wydawcy). Jeśli inne klasy lub struktury subskrybują zdarzenie, ich metody obsługi zdarzeń zostaną wywołane, gdy klasa wydawcy wywołuje zdarzenie. Aby uzyskać więcej informacji i przykłady kodu, zobacz [Zdarzenia](../../programming-guide/events/index.md) i [delegatów](../../programming-guide/delegates/index.md).

Zdarzenia mogą być oznaczone jako [publiczne,](./public.md) [prywatne,](./private.md) [chronione,](./protected.md) [wewnętrzne,](./internal.md) [chronione wewnętrzne](./protected-internal.md)lub [prywatne chronione.](./private-protected.md) Te modyfikatory dostępu definiują, w jaki sposób użytkownicy klasy mogą uzyskiwać dostęp do zdarzenia. Aby uzyskać więcej informacji, zobacz [Modyfikatory dostępu](../../programming-guide/classes-and-structs/access-modifiers.md).

## <a name="keywords-and-events"></a>Słowa kluczowe i wydarzenia

Następujące słowa kluczowe mają zastosowanie do zdarzeń.

|Słowo kluczowe|Opis|Więcej informacji|
|-------------|-----------------|--------------------------|
|[Statyczne](./static.md)|Udostępnia zdarzenie dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy.|[Klasy statyczne i statyczni członkowie klas](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md)|
|[virtual](./virtual.md)|Umożliwia klas pochodnych, aby zastąpić zachowanie zdarzenia przy użyciu [przesłonięcia](./override.md) słowa kluczowego.|[Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md)|
|[sealed](./sealed.md)|Określa, że dla klas pochodnych nie jest już wirtualny.||
|[Abstrakcja](./abstract.md)|Kompilator nie `add` będzie `remove` generować bloki akcesora i zdarzenia i dlatego klasy pochodne muszą zapewnić własną implementację.||

Zdarzenie może być zadeklarowane jako zdarzenie statyczne przy użyciu słowa kluczowego [statycznego.](./static.md) Dzięki temu zdarzenie jest dostępne dla wywoływania w dowolnym momencie, nawet jeśli nie istnieje żadne wystąpienie klasy. Aby uzyskać więcej informacji, zobacz [Klasy statyczne i elementy członkowskie klasy statycznej](../../programming-guide/classes-and-structs/static-classes-and-static-class-members.md).

Zdarzenie można oznaczyć jako zdarzenie wirtualne przy użyciu [wirtualnego](./virtual.md) słowa kluczowego. Dzięki temu klasy pochodne zastąpić zachowanie zdarzenia przy użyciu [przesłonięcia](./override.md) słowa kluczowego. Aby uzyskać więcej informacji, zobacz [Dziedziczenie](../../programming-guide/classes-and-structs/inheritance.md). Zdarzenie zastępujące zdarzenie wirtualne może być również [zapieczętowane,](./sealed.md)co określa, że dla klas pochodnych nie jest już wirtualny. Wreszcie zdarzenie może być [zadeklarowane jako abstrakcyjne](./abstract.md), co `add` `remove` oznacza, że kompilator nie wygeneruje bloków akcesora i zdarzenia. W związku z tym klasy pochodne muszą zapewnić własną implementację.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [Dodaj](./add.md)
- [Usunąć](./remove.md)
- [Modyfikatory](index.md)
- [Jak połączyć delegatów (delegatów multiemisji)](../../programming-guide/delegates/how-to-combine-delegates-multicast-delegates.md)
