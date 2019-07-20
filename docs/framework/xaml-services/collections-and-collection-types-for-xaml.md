---
title: Kolekcje i typy kolekcji dla XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 63f6346837f77dbdbdcb4a90ec5af725be69ee02
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2019
ms.locfileid: "68364338"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekcje i typy kolekcji dla XAML

W tym temacie opisano sposób definiowania właściwości typów, które są przeznaczone do obsługi kolekcji, oraz do obsługi składni XAML na potrzeby tworzenia wystąpień elementów kolekcji jako elementów podrzędnych elementu nadrzędnego obiektu lub właściwości.

## <a name="xaml-collection-concepts"></a>Pojęcia dotyczące kolekcji XAML

Koncepcyjnie, wszelkie relacje w języku XAML, w których istnieje wiele elementów podrzędnych w zakresie elementu obiektu XAML lub elementu właściwości XAML, muszą być zaimplementowane jako kolekcja. Ta kolekcja musi być skojarzona z określoną właściwością XAML typu XAML, który jest elementem nadrzędnym w tej relacji. Właściwość musi być kolekcją, ponieważ procesor XAML oczekuje, że każdy element w znaczniku zostanie przypisany do nowo dodanego elementu we właściwości kolekcji zapasowej.

Na poziomie języka XAML dokładne wymagania dotyczące obsługi kolekcji nie są w pełni zdefiniowane. Koncepcja, którą kolekcja może być listą lub Słownikiem (ale nie obu), jest zdefiniowana na poziomie języka XAML, ale typy zapasowe reprezentujące listy lub słowniki nie są zdefiniowane przez język XAML.

W .NET Framework usługach XAML pojęcie obsługi kolekcji XAML jest dokładniej zdefiniowane w warunkach .NET Framework typów zapasowych. W odróżnieniu od języka XAML dla kolekcji są oparte kilka .NET Framework pojęć i interfejsów API, które są używane dla list i słowników w ogólnym programowaniu .NET Framework.

1. <xref:System.Collections.IList> Interfejs wskazuje kolekcję list.

2. <xref:System.Collections.IDictionary> Interfejs wskazuje kolekcję słowników.

3. <xref:System.Array>reprezentuje tablicę, a tablica obsługuje <xref:System.Collections.IList> metody.

W każdym z tych pojęć związanych z zbieraniem danych moduł XAML usług XAML Services .NET Framework oczekuje wywołania `Add` metody dla określonego wystąpienia typu właściwości kolekcji. Lub w scenariuszu serializacji, procesor XAML produkuje dyskretne wystąpienia typu XAML dla każdego elementu znalezionego na liście, słowniku lub tablicy na podstawie konkretnej koncepcji kolekcji "Items". Są to: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; jawne<xref:System.Array.System%23Collections%23IList%23Item%2A> dla .<xref:System.Array>

## <a name="generic-collections"></a>Kolekcje ogólne

Kolekcje ogólne mogą być przydatne do ogólnego programowania .NET Framework i mogą być również używane dla właściwości kolekcji XAML. Jednak interfejsy <xref:System.Collections.Generic.IList%601> generyczne i <xref:System.Collections.Generic.IDictionary%602> nie są identyfikowane przez .NET Framework procesorów XAML usług XAML jako równoważne z nieogólnym <xref:System.Collections.IList> lub <xref:System.Collections.IDictionary>. Zamiast implementowania interfejsów Zalecanym podejściem do typów właściwości kolekcji ogólnej jest wyprowadzanie z klas <xref:System.Collections.Generic.List%601> lub. <xref:System.Collections.Generic.Dictionary%602> Te klasy implementują interfejsy inne niż ogólne, a tym samym obejmują oczekiwaną obsługę kolekcji XAML w implementacji podstawowej.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekcje i inicjalizacje tylko do odczytu

W .NET Framework programowaniu, jest to typowy Wzorzec projektowy, aby wykonać każdą właściwość, która przechowuje wartość kolekcji jako kolekcji tylko do odczytu. Ten wzorzec zezwala na wystąpienie, które jest właścicielem właściwości kolekcji, aby lepiej kontrolować, co się dzieje z kolekcją... W związku z tym wzorzec zapobiega przypadkowemu zastąpieniu całej istniejącej kolekcji przez ustawienie właściwości. W tym wzorcu każdy dostęp do kolekcji przez wywołujących powinien być wykonywany przez wywoływanie metod lub właściwości, które są obsługiwane przez typ kolekcji i/lub odpowiednie interfejsy kolekcji, takie jak <xref:System.Collections.IList>.

Użycie tego wzorca oznacza, że każda klasa, która ujawnia Właściwość kolekcji tylko do odczytu, musi najpierw zainicjować tę właściwość w celu przechowywania pustej kolekcji. Zazwyczaj inicjowanie jest wykonywane w ramach konstrukcji zachowań klasy. Aby można było użyć języka XAML, ważne jest, aby taka logika była zawsze przywoływana przez Konstruktor bez parametrów, ponieważ język XAML zwykle wywołuje Konstruktor bez parametrów, przed przetworzeniem właściwości (właściwości kolekcji lub w inny sposób).

## <a name="xaml-type-system-support-and-collections"></a>Obsługa i kolekcje systemu typu XAML

Poza podstawową Mechanics analizowania kodu XAML i wypełniania lub serializowania właściwości kolekcji, system typu XAML zgodnie z implementacją w .NET Framework usługach XAML zawiera kilka funkcji projektowania, które odnoszą się do kolekcji w języku XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>Zwraca wartość true, jeśli typ XAML jest obsługiwany przez typ, który zapewnia obsługę kolekcji XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>i <xref:System.Xaml.XamlType.IsArray%2A> można w dalszej sposób zidentyfikować tryb kolekcji obsługiwany przez typ XAML. W przypadku niestandardowych procesorów XAML opartych na .NET Framework usługach XAML i system typów XAML, ale nie opartych na <xref:System.Xaml.XamlWriter> istniejących implementacjach, wiedząc, który tryb zbierania danych może być niezbędny do poznania metody wywołania przetwarzanie kolekcji.

3. Każda z poprzednich wartości właściwości może mieć wpływ <xref:System.Xaml.XamlType.LookupCollectionKind%2A> na zastąpienia typu XAML.
