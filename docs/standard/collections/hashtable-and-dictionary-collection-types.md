---
title: Typy kolekcji tablic wartości funkcji mieszającej i słowników
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- Hashtable class, grouping data in collections
- Hashtable collection type
- hash tables
- grouping data in collections, Hashtable collection type
- hash function
- collections [.NET Framework], Hashtable collection type
ms.assetid: bfc20837-3d02-4fc7-8a8f-c5215b6b7913
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b4dde57e03e26085d19099e749afd50ba14874a5
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44063962"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekcji tablic wartości funkcji mieszającej i słowników
<xref:System.Collections.Hashtable?displayProperty=nameWithType> Klasy, a <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> Implementowanie klas ogólnych <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejsu. <xref:System.Collections.Generic.Dictionary%602> Implementuje również klasy ogólnej <xref:System.Collections.Generic.IDictionary%602> interfejs generyczny. W związku z tym każdy element w tych kolekcjach jest pary klucz wartość.  
  
 A <xref:System.Collections.Hashtable> obiekt składa się z zasobników, które zawierają elementy kolekcji. Zasobnik jest wirtualny podgrupę elementów w obrębie <xref:System.Collections.Hashtable>, co sprawia, że wyszukiwanie i pobieranie łatwiejsze i szybsze niż w większość kolekcji. Każdego przedziału jest skojarzony z skrótu, który jest generowany przy użyciu funkcji skrótu i opiera się na klucz elementu.  
  
 Ogólny <xref:System.Collections.Generic.HashSet%601> klasa jest nieuporządkowanej kolekcji do przechowywania unikatowych elementów.  
  
 Funkcja wyznaczania wartości skrótu jest algorytm, który zwraca wartość liczbową skrótu na podstawie klucza. Klucz jest wartość niektórych właściwości obiektu są przechowywane. Funkcja wyznaczania wartości skrótu musi zwracać zawsze tę samą wartość skrótu dla tego samego klucza. Istnieje możliwość dla funkcji skrótu, aby wygenerować tę samą wartość skrótu dla dwóch różnych kluczy, ale funkcja wyznaczania wartości skrótu, która generuje unikatową wartość skrótu dla poszczególnych unikatowych kluczy wyniki lepszą wydajność, podczas pobierania elementów z tablicy skrótów.  
  
 Każdy obiekt, który jest używany jako element w <xref:System.Collections.Hashtable> musi być w stanie wygenerować wartość skrótu dla siebie przy użyciu implementacji z <xref:System.Object.GetHashCode%2A> metody. Jednak można również określić funkcji skrótu dla wszystkich elementów w <xref:System.Collections.Hashtable> przy użyciu <xref:System.Collections.Hashtable> Konstruktor, który akceptuje <xref:System.Collections.IHashCodeProvider> implementacji jako jeden z jego parametrów.  
  
 Po dodaniu obiektu do <xref:System.Collections.Hashtable>, są przechowywane w zasobniku, który jest skojarzony z kodem skrótu, który dopasowuje wartość skrótu obiektu. Jeśli wartość jest wyszukiwana w <xref:System.Collections.Hashtable>skrótu jest generowany dla tej wartości i zostanie przeszukany zasobnika skojarzony z tym kodem skrótu.  
  
 Na przykład funkcję mieszania dla ciągu może potrwać kodów ASCII każdego znaku w ciągu i dodać je ze sobą, aby wygenerować wartość skrótu. Ciąg "piknik" miałyby kod skrótu, który jest inny niż wartość skrótu dla ciągów "koszyka"; w związku z tym ciągi "piknik" i "koszyka" będzie należeć do różnych przedziałów. Z kolei "podkreślić" i "desery" miałyby tę samą wartość skrótu i będzie mieć tego samego zasobnika.  
  
 <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klasy mają taką samą funkcjonalność jak <xref:System.Collections.Hashtable> klasy. A <xref:System.Collections.Generic.Dictionary%602> określonego typu (inne niż <xref:System.Object>) zapewnia lepszą wydajność niż <xref:System.Collections.Hashtable> dla typów wartości. Jest to spowodowane elementy <xref:System.Collections.Hashtable> typu <xref:System.Object>; w związku z tym, opakowywanie i rozpakowywanie zazwyczaj występują, gdy przechowywania lub pobrać typu wartości. <xref:System.Collections.Concurrent.ConcurrentDictionary%602> Klasy powinny być używane, gdy wiele wątków może uzyskiwać dostęp do kolekcji jednocześnie.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Hashtable>  
- <xref:System.Collections.IDictionary>  
- <xref:System.Collections.IHashCodeProvider>  
- <xref:System.Collections.Generic.Dictionary%602>  
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>  
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>  
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
