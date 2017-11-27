---
title: Kolekcje i typy kolekcji dla XAML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58f8e7c6-9a41-4f25-8551-c042f1315baa
caps.latest.revision: "2"
author: wadepickett
ms.author: wpickett
manager: wpickett
ms.openlocfilehash: 991360433b5fb09c13e59f63be94e0fa0ec94b61
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="collections-and-collection-types-for-xaml"></a>Kolekcje i typy kolekcji dla XAML
W tym temacie opisano sposób definiowania właściwości typów, które są przeznaczone do obsługi kolekcji, a także do obsługi składni języka XAML dla wystąpienia elementy kolekcji jako elementy podrzędne elementu nadrzędnego obiektu lub właściwości elementu.  
  
## <a name="xaml-collection-concepts"></a>Pojęcia dotyczące kolekcji XAML  
 Koncepcyjnie żadnej z relacji w kodzie XAML, gdzie istnieje wiele elementów podrzędnych w zakresie XAML object element lub element właściwości XAML muszą zostać zaimplementowane jako kolekcja. Tej kolekcji musi być skojarzona z właściwością XAML określonego typu XAML, który jest nadrzędny w tej relacji. Właściwość musi być kolekcją, ponieważ procesor XAML oczekuje można przypisać każdego elementu w znaczniku jako nowo dodanego elementu zapasowy właściwości kolekcji.  
  
 Na poziomie języka XAML dokładne wymagania dotyczące obsługi kolekcji nie są całkowicie zdefiniowane. Koncepcji, że kolekcja może być albo listy lub słownika (ale nie oba) jest zdefiniowana na poziomie języka XAML, ale typy zapasowy, które reprezentują albo list lub słowników nie jest zdefiniowany w języku XAML.  
  
 W programie .NET Framework XAML Services pojęcie XAML Obsługa kolekcji jest więcej jasno określone pod względem .NET Framework kopii typów. W szczególności XAML obsługę kolekcje opiera się na kilka pojęć .NET Framework i interfejsów API, które są używane w przypadku list i słowników w ogólne programowania .NET Framework.  
  
1.  <xref:System.Collections.IList> Interfejsu wskazuje kolekcji list.  
  
2.  <xref:System.Collections.IDictionary> Interfejsu wskazuje dicionary kolekcji.  
  
3.  <xref:System.Array>reprezentuje tablicę i tablicy obsługuje <xref:System.Collections.IList> metody.  
  
 W każdym z tych pojęć kolekcji procesora .NET Framework XAML Services XAML oczekuje, że wywołanie `Add` metody na określonym wystąpieniu typu właściwości kolekcji. Lub, w przypadku serializacji, procesor XAML tworzy osobne wystąpienia typu XAML dla każdego elementu listy, słownika lub tablicy oparte na każdej kolekcji specyficzną koncepcję "Elementów". Są to: <xref:System.Collections.IList.Item%2A>; <xref:System.Collections.IDictionary.Item%2A>; jawnych <xref:System.Array.System%23Collections%23IList%23Item%2A> dla <xref:System.Array>.  
  
## <a name="generic-collections"></a>Kolekcje ogólne  
 Kolekcje ogólne mogą być przydatne podczas programowania ogólne .NET Framework i może również służyć do właściwości kolekcji XAML. Jednak ogólnych interfejsów <xref:System.Collections.Generic.IList%601> i <xref:System.Collections.Generic.IDictionary%602> nie są identyfikowane przez .NET Framework XAML Services XAML procesorów jako równoważne nieogólnego <xref:System.Collections.IList> lub <xref:System.Collections.IDictionary>. Zamiast implementacji interfejsów, zalecane podejście do typy kolekcji ogólnych właściwości ma pochodzić od klasy <xref:System.Collections.Generic.List%601> lub <xref:System.Collections.Generic.Dictionary%602>. Te klasy implementować interfejsów nieogólnego i w związku z tym obejmują oczekiwanego obsługę kolekcje XAML w implementacji podstawowej.  
  
## <a name="read-only-collections-and-initialization-logic"></a>Kolekcji tylko do odczytu i logikę inicjującą  
 W programie .NET Framework programowania jest wspólnego wzorca projektowego dokonanie dowolnej właściwości, która zawiera wartość z kolekcji jako kolekcji tylko do odczytu. Ten wzorzec zezwala na wystąpienie, które należą do lepszą kontrolę, co się dzieje z kolekcji właściwości kolekcji. W szczególności wzorzec zapobiega przypadkowemu zastąpienie istniejącego całą kolekcję przez ustawienie właściwości. W tym wzorcu dostęp do kolekcji przez obiekty wywołujące zamiast tego należy ustanowić przez wywołanie metody lub właściwości obsługiwana przez typ kolekcji i/lub interfejsy odpowiednich kolekcji, takie jak <xref:System.Collections.IList>.  
  
 Za pomocą tego wzorca oznacza, że każdej klasy, która udostępnia właściwości kolekcji tylko do odczytu najpierw należy zainicjować tej właściwości, aby pomieścić pustą kolekcję. Zwykle inicjowania jest wykonywane jako część konstrukcji zachowanie dla klasy. Powinna być użyteczna dla XAML, jest ważne, że takie logiki zawsze odwołuje się konstruktora domyślnego ponieważ XAML zazwyczaj wywołuje konstruktor domyślny przed przetworzeniem właściwości (właściwości kolekcji lub w inny sposób).  
  
## <a name="xaml-type-system-support-and-collections"></a>Obsługa systemu typu XAML i kolekcji  
 Poza podstawowa mechanika analizowania XAML i wypełnianie lub serializowania właściwości kolekcji system typów języka XAML zgodnie z implementacją w .NET Framework XAML Services zawiera kilka funkcji projektowania odnoszą się do kolekcji w języku XAML.  
  
1.  <xref:System.Xaml.XamlType.IsCollection%2A>Zwraca wartość true, jeśli typ XAML nie jest obsługiwana przez typ, który zapewnia obsługę kolekcji XAML.  
  
2.  <xref:System.Xaml.XamlType.IsDictionary%2A>i <xref:System.Xaml.XamlType.IsArray%2A> dalsze zidentyfikuje, który typ XAML obsługuje tryb kolekcji. Dla XAML niestandardowych procesorów, które są oparte na usług .NET Framework XAML i XAML system typów, ale nie jest oparty na istniejących <xref:System.Xaml.XamlWriter> implementacji, wiedząc, który tryb kolekcji jest używany może być konieczne, aby wiedzieć, którego metoda do wywołania dla Przetwarzanie kolekcji.  
  
3.  Poprzednie wartości właściwości potencjalnie wpływało przesłonięcia <xref:System.Xaml.XamlType.LookupCollectionKind%2A> typu XAML.
