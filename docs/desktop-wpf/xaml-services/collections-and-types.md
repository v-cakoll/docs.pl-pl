---
title: Kolekcje i typy kolekcji dla XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 2ec58026c605df31489c8aab4c4cc714dab11474
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "82071298"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekcje i typy kolekcji dla XAML

W tym artykule opisano sposób definiowania właściwości typów, które są przeznaczone do obsługi kolekcji i do obsługi składni XAML do tworzenia wystąpienia elementów kolekcji jako elementy podrzędne elementu nadrzędnego elementu obiektu lub elementu właściwości.

## <a name="xaml-collection-concepts"></a>Pojęcia dotyczące kolekcji XAML

Koncepcyjnie każda relacja w języku XAML, gdzie istnieje wiele elementów podrzędnych w zakresie elementu obiektu XAML lub elementu właściwości XAML, musi zostać zaimplementowana jako kolekcja. Ta kolekcja musi być skojarzona z określoną właściwością XAML typu XAML, która jest elementem nadrzędnym w tej relacji. Właściwość musi być kolekcją, ponieważ procesor XAML oczekuje przypisania każdego elementu w znacznikach jako nowo dodanego elementu właściwości kolekcji kopii zapasowej.

Na poziomie języka XAML dokładne wymagania obsługi kolekcji nie są w pełni zdefiniowane. Koncepcja, że kolekcja może być listą lub słownikiem(ale nie oba) jest zdefiniowana na poziomie języka XAML, ale które typy kopii reprezentują listy lub słowniki nie jest zdefiniowana przez język XAML.

W usługach .NET XAML koncepcja obsługi kolekcji XAML jest jaśniej zdefiniowana pod względem typów kopii .NET. W szczególności obsługa XAML dla kolekcji opiera się na kilku pojęciach platformy .NET i interfejsach API, które są używane dla list i słowników w ogóle programowania .NET.

1. Interfejs <xref:System.Collections.IList> wskazuje kolekcję listy.

2. Interfejs <xref:System.Collections.IDictionary> wskazuje kolekcję słownika.

3. <xref:System.Array>reprezentuje tablicę, a <xref:System.Collections.IList> tablica obsługuje metody.

W każdej z tych koncepcji kolekcji procesor XAML usług .NET `Add` XAML oczekuje wywołania metody w określonym wystąpieniu typu właściwości kolekcji. Lub w scenariuszu serializacji procesor XAML tworzy dyskretne wystąpienia typu XAML dla każdego elementu znajdującego się na liście, słowniku lub tablicy na podstawie określonej koncepcji każdej kolekcji "Elementy". Te elementy <xref:System.Collections.IList.Item%2A?displayProperty=nameWithType>to: ; <xref:System.Collections.IDictionary.Item%2A?displayProperty=nameWithType>; wyraźne <xref:System.Array.System%23Collections%23IList%23Item%2A?displayProperty=nameWithType> dla <xref:System.Array>.

## <a name="generic-collections"></a>Kolekcje ogólne

Kolekcje ogólne mogą być przydatne do ogólnego programowania .NET i mogą być również używane dla właściwości kolekcji XAML. Jednak <xref:System.Collections.Generic.IList%601> interfejsy ogólne <xref:System.Collections.Generic.IDictionary%602> i nie są identyfikowane przez procesory XAML usług .NET <xref:System.Collections.IList> XAML jako równoważne z nieogólnym lub <xref:System.Collections.IDictionary>. Zamiast implementować interfejsy, zalecane podejście dla typów właściwości kolekcji rodzajowej jest pochodzić z klas <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>. Te klasy implementują interfejsy nieogólne i w związku z tym obejmują oczekiwaną obsługę kolekcji XAML w implementacji podstawowej.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekcje tylko do odczytu i logika inicjowania

W programowaniu .NET jest typowym wzorcem projektu, aby każda właściwość, która przechowuje wartość kolekcji jako kolekcji tylko do odczytu. Ten wzorzec zezwala na wystąpienie, które jest właścicielem właściwości kolekcji, aby lepiej kontrolować, co dzieje się z kolekcji.. W szczególności wzorzec zapobiega przypadkowej wymianie całej istniejącej kolekcji przez ustawienie właściwości. W tym wzorcu każdy dostęp do kolekcji przez obiekty wywołujące powinien być zamiast tego dokonywany przez wywoływanie metod <xref:System.Collections.IList>lub właściwości obsługiwanych przez typ kolekcji i/lub odpowiednie interfejsy kolekcji, takie jak .

Za pomocą tego wzorca oznacza, że każda klasa, która udostępnia właściwość kolekcji tylko do odczytu musi najpierw zainicjować tej właściwości do przechowywania pustej kolekcji. Zazwyczaj inicjowanie jest wykonywane jako część zachowania konstrukcji dla klasy. Aby być przydatne dla XAML, ważne jest, że taka logika jest zawsze odwołuje się do konstruktora bez parametrów, ponieważ XAML zazwyczaj wywołuje konstruktora bez parametrów przed przetworzeniem właściwości (właściwości kolekcji lub w inny sposób).

## <a name="xaml-type-system-support-and-collections"></a>Obsługa i kolekcje systemu typu XAML

Oprócz podstawowej mechaniki analizowania XAML i wypełniania lub serializacji właściwości kolekcji, system typu XAML zaimplementowany w usługach .NET XAML zawiera kilka funkcji projektowych, które odnoszą się do kolekcji w języku XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A>zwraca wartość true, jeśli typ XAML jest wspierany przez typ, który zapewnia obsługę kolekcji XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A>i <xref:System.Xaml.XamlType.IsArray%2A> może dodatkowo określić, który tryb zbierania obsługuje typ XAML. W przypadku niestandardowych procesorów XAML, które są oparte na usługach .NET XAML Services i systemie typu XAML, ale nie na podstawie istniejących <xref:System.Xaml.XamlWriter> implementacji, wiedza o tym, który tryb zbierania jest używany, może być konieczna, aby wiedzieć, która metoda ma zostać wywołana do przetwarzania kolekcji.

3. Na każdą z poprzednich wartości właściwości mogą mieć <xref:System.Xaml.XamlType.LookupCollectionKind%2A> wpływ zastąpienia typu XAML.
