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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711379"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekcji tablic wartości funkcji mieszającej i słowników
Klasa <xref:System.Collections.Hashtable?displayProperty=nameWithType> oraz klasy ogólne <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> implementują interfejs <xref:System.Collections.IDictionary?displayProperty=nameWithType>. Klasa ogólna <xref:System.Collections.Generic.Dictionary%602> również implementuje interfejs ogólny <xref:System.Collections.Generic.IDictionary%602>. W związku z tym każdy element w tych kolekcjach jest parą klucz-wartość.  
  
 Obiekt <xref:System.Collections.Hashtable> składa się z zasobników zawierających elementy kolekcji. Zasobnik jest podgrupą wirtualną elementów w <xref:System.Collections.Hashtable>, co sprawia, że wyszukiwanie i pobieranie jest łatwiejsze i szybsze niż w większości kolekcji. Każdy zasobnik jest skojarzony z kodem skrótu, który jest generowany przy użyciu funkcji skrótu i jest oparty na kluczu elementu.  
  
 Klasa generyczna <xref:System.Collections.Generic.HashSet%601> jest nieuporządkowaną kolekcją zawierającą unikatowe elementy.  
  
 Funkcja skrótu jest algorytmem zwracającym kod skrótu numerycznego na podstawie klucza. Klucz jest wartością pewnej właściwości przechowywanego obiektu. Funkcja skrótu musi zawsze zwracać ten sam kod skrótu dla tego samego klucza. Jest możliwe, aby funkcja skrótu generowała ten sam kod skrótu dla dwóch różnych kluczy, ale funkcja skrótu generująca unikatowy kod skrótu dla każdego unikatowego klucza skutkuje lepszą wydajnością podczas pobierania elementów z tabeli skrótów.  
  
 Każdy obiekt, który jest używany jako element w <xref:System.Collections.Hashtable> musi mieć możliwość wygenerowania kodu skrótu dla samego siebie przy użyciu implementacji metody <xref:System.Object.GetHashCode%2A>. Można jednak również określić funkcję skrótu dla wszystkich elementów w <xref:System.Collections.Hashtable> przy użyciu konstruktora <xref:System.Collections.Hashtable>, który akceptuje implementację <xref:System.Collections.IHashCodeProvider> jako jeden z jej parametrów.  
  
 Gdy obiekt jest dodawany do <xref:System.Collections.Hashtable>, jest przechowywany w zasobniku, który jest skojarzony z kodem skrótu, który pasuje do kodu skrótu obiektu. Gdy wartość jest wyszukiwana w <xref:System.Collections.Hashtable>, dla tej wartości jest generowany kod skrótu i przeszukiwany jest zasobnik skojarzony z tym kodem skrótu.  
  
 Na przykład funkcja skrótu dla ciągu może przyjmować kody ASCII każdego znaku w ciągu i dodawać je w celu wygenerowania kodu skrótu. Ciąg "piknik" będzie miał kod skrótu, który różni się od kodu skrótu dla ciągu "koszyk"; w związku z tym ciągi "piknik" i "koszyk" byłyby w różnych zasobnikach. Z kolei "stresd" i "Desserts" będą mieć ten sam kod skrótu i znajdować się w tym samym przedziale.  
  
 Klasy <xref:System.Collections.Generic.Dictionary%602> i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> mają takie same funkcje jak Klasa <xref:System.Collections.Hashtable>. <xref:System.Collections.Generic.Dictionary%602> określonego typu (inny niż <xref:System.Object>) zapewnia lepszą wydajność niż <xref:System.Collections.Hashtable> dla typów wartości. Dzieje się tak, ponieważ elementy <xref:System.Collections.Hashtable> są typu <xref:System.Object>; w związku z tym opakowanie i rozpakowywanie zwykle występuje w przypadku przechowywania lub pobierania typu wartości. Klasy <xref:System.Collections.Concurrent.ConcurrentDictionary%602> należy używać, gdy wiele wątków może jednocześnie uzyskać dostęp do kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Często używane typy kolekcji](../../../docs/standard/collections/commonly-used-collection-types.md)
