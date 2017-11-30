---
title: "Typy kolekcji tablic wartości funkcji mieszającej i słowników"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
caps.latest.revision: "16"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: aa2392775f0bd2d68c0aeb28aa0654b690b11808
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekcji tablic wartości funkcji mieszającej i słowników
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Klasy, a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> implementuje klasy ogólne <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejsu. <xref:System.Collections.Generic.Dictionary%602> Implementuje również klasy ogólnej <xref:System.Collections.Generic.IDictionary%602> interfejs generyczny. W związku z tym każdy element w tych kolekcjach jest parę klucza i wartości.  
  
 A <xref:System.Collections.Hashtable> obiekt składa się z pakiety, które zawierają elementy kolekcji. Zasobnik jest wirtualnego podgrupy elementów w <xref:System.Collections.Hashtable>, co czyni wyszukiwanie i pobieranie łatwiejsze i szybsze niż w większość kolekcji. Każdy zasobnika jest skojarzony z skrótu, który jest generowany przy użyciu funkcji skrótu i jest oparta na klucz elementu.  
  
 Ogólnego <xref:System.Collections.Generic.HashSet%601> klasy jest nieuporządkowaną kolekcji dla zawierających elementy unikatowe.  
  
 Funkcja wyznaczania wartości skrótu jest algorytmem, który zwraca wartość liczbową skrótu oparte na kluczu. Klucz jest wartość niektórych właściwości obiektu są przechowywane. Funkcja wyznaczania wartości skrótu zawsze musi zwracać taki sam skrót tego samego klucza. Istnieje możliwość dla funkcji skrótu, aby wygenerować ten sam kod skrótu dla dwóch różnych kluczy, ale funkcji skrótu, który generuje unikatową wartość skrótu dla każdego unikatowy kluczy wyniki lepszą wydajność podczas pobierania elementów z tablicy skrótów.  
  
 Każdy obiekt, który jest używany jako element <xref:System.Collections.Hashtable> musi być w stanie wygenerować skrótu dla siebie przy użyciu implementacja <xref:System.Object.GetHashCode%2A> metody. Jednak można również określić funkcji skrótu dla wszystkich elementów w <xref:System.Collections.Hashtable> za pomocą <xref:System.Collections.Hashtable> konstruktora akceptującego <xref:System.Collections.IHashCodeProvider> implementacji jako jeden z jego parametrów.  
  
 Po dodaniu do obiektu <xref:System.Collections.Hashtable>, znajduje się w przedziale, skojarzony z skrótu odpowiadającego obiektu skrótu. Jeśli wartości są wyszukiwane w <xref:System.Collections.Hashtable>skrótu jest generowany dla tej wartości i zasobnik skojarzony z tym skrótu jest przeszukiwany.  
  
 Na przykład funkcji skrótu ciągu może potrwać kodów ASCII każdego znaku w ciągu i dodaj je ze sobą w celu generowania skrótu. Ciąg "piknik" miałyby skrótu jest inna niż wartość skrótu dla ciągu "koszyk"; w związku z tym ciągów "piknik" oraz "koszyk" będą się w różnych zasobników. Z kolei "zawsze" i "desery" będzie mieć taki sam skrót i będzie w tym samym przedziale.  
  
 <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klasy mają te same funkcje co <xref:System.Collections.Hashtable> klasy. A <xref:System.Collections.Generic.Dictionary%602> określonego typu (inne niż <xref:System.Object>) zapewnia lepszą wydajność niż <xref:System.Collections.Hashtable> dla typów wartości. Jest to spowodowane elementy <xref:System.Collections.Hashtable> typu <xref:System.Object>; w związku z tym opakowywanie i rozpakowywanie zazwyczaj występuje podczas przechowywania lub pobrać typu wartości. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Klasa powinna być używana, jeśli wiele wątków może być jednocześnie dostęp do kolekcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.Hashtable>  
 <xref:System.Collections.IDictionary>  
 <xref:System.Collections.IHashCodeProvider>  
 <xref:System.Collections.Generic.Dictionary%602>  
 <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
 <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>  
 [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
