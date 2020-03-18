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
ms.openlocfilehash: a6f234b6205fd30507b9342d9839db6adcddfc2e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711379"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekcji tablic wartości funkcji mieszającej i słowników
Klasa <xref:System.Collections.Hashtable?displayProperty=nameWithType> i <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> klasy <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> ogólne i ogólne <xref:System.Collections.IDictionary?displayProperty=nameWithType> implementują interfejs. Klasa <xref:System.Collections.Generic.Dictionary%602> ogólna implementuje <xref:System.Collections.Generic.IDictionary%602> również interfejs ogólny. W związku z tym każdy element w tych kolekcjach jest para klucz i wartość.  
  
 Obiekt <xref:System.Collections.Hashtable> składa się z zasobników, które zawierają elementy kolekcji. Zasobnik jest wirtualną podgrupą <xref:System.Collections.Hashtable>elementów w ramach programu , co sprawia, że wyszukiwanie i pobieranie jest łatwiejsze i szybsze niż w większości kolekcji. Każdy zasobnik jest skojarzony z kodem mieszania, który jest generowany przy użyciu funkcji mieszania i jest oparty na kluczu elementu.  
  
 Klasa <xref:System.Collections.Generic.HashSet%601> ogólna jest nieuporządkowaną kolekcją zawierającą unikatowe elementy.  
  
 Funkcja mieszania jest algorytmem, który zwraca numeryczny kod skrótu na podstawie klucza. Klucz jest wartością niektórych właściwości obiektu przechowywane. Funkcja mieszania musi zawsze zwracać ten sam kod skrótu dla tego samego klucza. Jest możliwe dla funkcji mieszania, aby wygenerować ten sam kod skrótu dla dwóch różnych kluczy, ale funkcja mieszania, która generuje unikatowy kod skrótu dla każdego unikatowego klucza powoduje lepszą wydajność podczas pobierania elementów z tabeli mieszania.  
  
 Każdy obiekt, który jest używany <xref:System.Collections.Hashtable> jako element w musi być w stanie wygenerować <xref:System.Object.GetHashCode%2A> kod skrótu dla siebie przy użyciu implementacji metody. Można jednak również określić funkcję mieszania dla wszystkich <xref:System.Collections.Hashtable> elementów <xref:System.Collections.Hashtable> w konstruktorze, który akceptuje <xref:System.Collections.IHashCodeProvider> implementację jako jeden z jej parametrów.  
  
 Po dodaniu obiektu <xref:System.Collections.Hashtable>do zasobnika jest on przechowywany w zasobniku skojarzonym z kodem mieszania, który pasuje do kodu skrótu obiektu. Gdy wartość jest wyszukiwana <xref:System.Collections.Hashtable>w , kod skrótu jest generowany dla tej wartości, a zasobnik skojarzony z tym kodem mieszania jest przeszukiwany.  
  
 Na przykład funkcja mieszania dla ciągu może podjąć kody ASCII każdego znaku w ciągu i dodać je razem, aby wygenerować kod skrótu. Ciąg "piknik" będzie miał kod skrótu, który różni się od kodu skrótu dla ciągu "koszyk"; dlatego struny "piknik" i "kosz" będą w różnych wiadrach. Natomiast "zestresowane" i "desery" miałyby ten sam kod mieszania i byłyby w tym samym wiadrze.  
  
 I <xref:System.Collections.Generic.Dictionary%602> <xref:System.Collections.Concurrent.ConcurrentDictionary%602> klasy mają taką samą <xref:System.Collections.Hashtable> funkcjonalność jak klasa. A <xref:System.Collections.Generic.Dictionary%602> określonego typu (inne <xref:System.Object>niż ) zapewnia <xref:System.Collections.Hashtable> lepszą wydajność niż dla typów wartości. Dzieje się tak, <xref:System.Collections.Hashtable> ponieważ <xref:System.Object>elementy są typu ; w związku z tym boks i rozpakowywanie zazwyczaj występują podczas przechowywania lub pobierania typu wartości. Klasa <xref:System.Collections.Concurrent.ConcurrentDictionary%602> powinna być używana, gdy wiele wątków może uzyskiwać dostęp do kolekcji jednocześnie.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
