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
ms.openlocfilehash: b228f5db16ba01969b77d601becfb94ac0506d1e
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287968"
---
# <a name="hashtable-and-dictionary-collection-types"></a>Typy kolekcji tablic wartości funkcji mieszającej i słowników
<xref:System.Collections.Hashtable?displayProperty=nameWithType>Klasa oraz <xref:System.Collections.Generic.Dictionary%602?displayProperty=nameWithType> klasy i i <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType> generyczne implementują <xref:System.Collections.IDictionary?displayProperty=nameWithType> interfejs. <xref:System.Collections.Generic.Dictionary%602>Klasa generyczna implementuje także <xref:System.Collections.Generic.IDictionary%602> interfejs ogólny. W związku z tym każdy element w tych kolekcjach jest parą klucz-wartość.  
  
 <xref:System.Collections.Hashtable>Obiekt składa się z zasobników zawierających elementy kolekcji. Zasobnik jest podgrupą wirtualną elementów w ramach <xref:System.Collections.Hashtable> , co sprawia, że wyszukiwanie i pobieranie jest łatwiejsze i szybsze niż w większości kolekcji. Każdy zasobnik jest skojarzony z kodem skrótu, który jest generowany przy użyciu funkcji skrótu i jest oparty na kluczu elementu.  
  
 Klasa generyczna <xref:System.Collections.Generic.HashSet%601> to nieuporządkowana Kolekcja zawierająca unikatowe elementy.  
  
 Funkcja skrótu jest algorytmem zwracającym kod skrótu numerycznego na podstawie klucza. Klucz jest wartością pewnej właściwości przechowywanego obiektu. Funkcja skrótu musi zawsze zwracać ten sam kod skrótu dla tego samego klucza. Jest możliwe, aby funkcja skrótu generowała ten sam kod skrótu dla dwóch różnych kluczy, ale funkcja skrótu generująca unikatowy kod skrótu dla każdego unikatowego klucza skutkuje lepszą wydajnością podczas pobierania elementów z tabeli skrótów.  
  
 Każdy obiekt, który jest używany jako element w, <xref:System.Collections.Hashtable> musi być w stanie wygenerować kod skrótu dla samego siebie przy użyciu implementacji <xref:System.Object.GetHashCode%2A> metody. Można jednak określić funkcję mieszania dla wszystkich elementów w a przy <xref:System.Collections.Hashtable> użyciu <xref:System.Collections.Hashtable> konstruktora, który akceptuje <xref:System.Collections.IHashCodeProvider> implementację jako jeden z jej parametrów.  
  
 Gdy obiekt jest dodawany do <xref:System.Collections.Hashtable> , jest przechowywany w zasobniku skojarzonym z kodem skrótu, który pasuje do kodu skrótu obiektu. Gdy wartość jest wyszukiwana w programie <xref:System.Collections.Hashtable> , dla tej wartości jest generowany kod skrótu i przeszukiwany jest zasobnik skojarzony z tym kodem skrótu.  
  
 Na przykład funkcja skrótu dla ciągu może przyjmować kody ASCII każdego znaku w ciągu i dodawać je w celu wygenerowania kodu skrótu. Ciąg "piknik" będzie miał kod skrótu, który różni się od kodu skrótu dla ciągu "koszyk"; w związku z tym ciągi "piknik" i "koszyk" byłyby w różnych zasobnikach. Z kolei "stresd" i "Desserts" będą mieć ten sam kod skrótu i znajdować się w tym samym przedziale.  
  
 <xref:System.Collections.Generic.Dictionary%602>Klasy i <xref:System.Collections.Concurrent.ConcurrentDictionary%602> mają takie same funkcje jak <xref:System.Collections.Hashtable> Klasa. <xref:System.Collections.Generic.Dictionary%602>Określony typ (inny niż <xref:System.Object> ) zapewnia lepszą wydajność niż <xref:System.Collections.Hashtable> w przypadku typów wartości. Jest to spowodowane tym, że elementy <xref:System.Collections.Hashtable> są typu <xref:System.Object> ; w związku z tym, opakowanie i rozpakowywanie zwykle występuje podczas przechowywania lub pobierania typu wartości. <xref:System.Collections.Concurrent.ConcurrentDictionary%602>Klasy należy używać, gdy wiele wątków może jednocześnie uzyskać dostęp do kolekcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.Hashtable>
- <xref:System.Collections.IDictionary>
- <xref:System.Collections.IHashCodeProvider>
- <xref:System.Collections.Generic.Dictionary%602>
- <xref:System.Collections.Generic.IDictionary%602?displayProperty=nameWithType>
- <xref:System.Collections.Concurrent.ConcurrentDictionary%602?displayProperty=nameWithType>
- [Często używane typy kolekcji](commonly-used-collection-types.md)
