---
title: Kolekcje i typy kolekcji dla XAML
ms.date: 03/30/2017
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
ms.openlocfilehash: 4123b64545f7c47a96c4cae496046a89b7e576b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61954183"
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekcje i typy kolekcji dla XAML

W tym temacie opisano sposób definiowania właściwości typów, które są przeznaczone do obsługi kolekcji oraz zapewnić obsługę składnia XAML podczas tworzenia wystąpienia elementów kolekcji jako elementy podrzędne elementu obiektu nadrzędnego lub element właściwości.

## <a name="xaml-collection-concepts"></a>Pojęcia dotyczące kolekcji XAML

Model żadnych relacji w XAML, gdzie wiele elementów podrzędnych w zakresie elementu obiektu XAML lub element właściwości XAML musi zostać wdrożony jako kolekcję. Tej kolekcji musi być skojarzona z właściwością XAML określonego typu XAML, który jest elementem nadrzędnym w tej relacji. Właściwość musi być kolekcją, ponieważ procesor XAML oczekuje, że można przypisać każdego elementu w znacznikach do nowo dodanego elementu właściwości kolekcji zapasowy.

Na poziomie języka XAML dokładne wymagania dotyczące obsługi kolekcji nie są w pełni zdefiniowane. Koncepcja, że kolekcja może być albo listy lub słownika (ale nie obu) jest zdefiniowana na poziomie języka XAML, ale typy zapasowy reprezentują obu list lub słowników nie jest zdefiniowany w języku XAML.

W programie .NET Framework XAML Services koncepcji obsługi kolekcji XAML wyraźniej zdefiniowano pod względem kopii typy w .NET Framework. W szczególności XAML Obsługa kolekcji opiera się na kilka pojęć programu .NET Framework i interfejsów API, które są używane w przypadku list i słowników w ogólne programowaniu .NET Framework.

1. <xref:System.Collections.IList> Interfejs wskazuje kolekcję listy.

2. <xref:System.Collections.IDictionary> Interfejs wskazuje kolekcję słownika.

3. <xref:System.Array> reprezentuje tablicę, a tablica obsługuje <xref:System.Collections.IList> metody.

W każdym z tych koncepcji zbierania procesora XAML Services programu .NET Framework XAML oczekuje, że wywołanie `Add` metody na określonym wystąpieniu typu właściwości kolekcji. Lub, w przypadku serializacji procesora XAML tworzy osobne wystąpienia typu XAML dla każdego elementu, na liście, słownika lub tablicy, w oparciu o określonych koncepcji "Items" w każdej kolekcji. Są to: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; jawne <xref:System.Array.System%23Collections%23IList%23Item%2A> dla <xref:System.Array>.

## <a name="generic-collections"></a>Kolekcje ogólne

Kolekcje ogólne mogą być przydatne w przypadku ogólnych .NET Framework programowania i może również służyć do właściwości kolekcji XAML. Jednak interfejsów ogólnych <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602> nie są identyfikowane przez procesory XAML Services programu .NET Framework XAML za równoważne niepodstawowy <xref:System.Collections.IList> lub <xref:System.Collections.IDictionary>. Zamiast implementacji interfejsów, dla typów właściwości kolekcji ogólnej zaleca się pochodzi od klasy <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>. W ramach tych zajęć implementować interfejsy nieogólnego i dlatego zawierać oczekiwanej pomocy technicznej dla kolekcji XAML w podstawowej implementacji.

## <a name="read-only-collections-and-initialization-logic"></a>Kolekcji tylko do odczytu i logiki inicjowania

W programie .NET Framework programowania jest typowy wzorzec projektowania nawiązać dowolnej właściwości, która przechowuje wartość kolekcji jako kolekcji tylko do odczytu. Ten wzorzec pozwala na wystąpienie, które jest właścicielem właściwość kolekcji lepszej kontroli, co się dzieje z kolekcji... W szczególności wzorzec uniemożliwia przypadkowe zastąpienie całej kolekcji istniejące, ustawiając właściwość. W tym wzorcu dostępu do kolekcji przez obiekty wywołujące zamiast tego należy ustanowić przez wywołanie metody lub właściwości, obsługiwana przez typ kolekcji i/lub interfejsy odpowiednich kolekcji, takich jak <xref:System.Collections.IList>.

Za pomocą tego wzorca oznacza, że każdej klasy, która udostępnia właściwości kolekcji tylko do odczytu najpierw należy zainicjować tę właściwość, aby pomieścić pustą kolekcję. Zazwyczaj Inicjalizacja jest wykonywana w ramach zachowanie konstrukcja w klasie. To przydatne w przypadku XAML, ważne jest czy takie logiki zawsze odwołuje się konstruktora domyślnego, ponieważ XAML ogólnie wywołuje konstruktor domyślny, przed rozpoczęciem przetwarzania właściwości (właściwości kolekcji lub w inny sposób).

## <a name="xaml-type-system-support-and-collections"></a>Obsługa systemie typu XAML i kolekcji

Poza podstawowa mechanika analiza kodu XAML i wypełnianie lub właściwości kolekcji serializacji systemie typu XAML zaimplementowanego w .NET Framework XAML Services udostępnia kilka funkcji projektowania, które odnoszą się do kolekcji w programie XAML.

1. <xref:System.Xaml.XamlType.IsCollection%2A> Zwraca wartość true, jeśli typ XAML jest wspierany przez typ, który zapewnia obsługę kolekcji XAML.

2. <xref:System.Xaml.XamlType.IsDictionary%2A> i <xref:System.Xaml.XamlType.IsArray%2A> dalsze można zidentyfikować tryb kolekcji, w którym typ XAML obsługuje. W przypadku niestandardowych XAML system typów procesorów, które są oparte na usług programu .NET Framework XAML i XAML, ale nie jest oparty na istniejących <xref:System.Xaml.XamlWriter> implementacje, wiedząc, używany jest tryb kolekcji, które mogą być niezbędne, aby dowiedzieć się, jakiej metody do wywołania dla Przetwarzanie kolekcji.

3. Każdy z poprzednimi wartościami właściwości potencjalnie wpływało zastąpień <xref:System.Xaml.XamlType.LookupCollectionKind%2A> typu XAML.
