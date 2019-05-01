---
title: Porównywanie i sortowanie w kolekcjach
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting data, collections
- IComparable.CompareTo method
- Collections classes
- Equals method
- collections [.NET Framework], comparisons
ms.assetid: 5e4d3b45-97f0-423c-a65f-c492ed40e73b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 45f0e30efac32dec42cf0687fa0da40f4d6dca4f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61909080"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porównywanie i sortowanie w kolekcjach
<xref:System.Collections> Klasy wykonania porównania w prawie wszystkich procesów zarządzania kolekcjami, czy wyszukiwanie elementu do usunięcia lub zwracania wartości parę klucza i wartości.  
  
 Kolekcje wykorzystywać zazwyczaj moduł porównujący równość i/lub szeregowania porównania. Konstrukcje dwa są używane do porównania.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Sprawdzanie pod kątem równości  
 Metody takie jak `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, i `Remove` moduł porównujący równość na użytek elementów kolekcji. Jeśli kolekcja jest ogólna, niż elementy są porównywane pod kątem równości, zgodnie z następującymi wytycznymi:  
  
- Jeśli typ T implementuje <xref:System.IEquatable%601> ogólny interfejs, a następnie moduł porównujący równość jest <xref:System.IEquatable%601.Equals%2A> metody tego interfejsu.  
  
- Jeśli typ T nie implementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> jest używany.  
  
 Ponadto niektóre przeciążenia konstruktora dla kolekcji słownika, Zaakceptuj <xref:System.Collections.Generic.IEqualityComparer%601> wdrażania, który służy do porównywania kluczy pod kątem równości. Aby uzyskać przykład, zobacz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktora.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Określanie kolejności sortowania  
 Metody takie jak `BinarySearch` i `Sort` szeregowania modułu porównującego na użytek elementów kolekcji. Porównania mogą być, między elementy kolekcji lub między elementem i określoną wartość. Porównywanie obiektów, jest koncepcji `default comparer` i `explicit comparer`.  
  
 Domyślny moduł porównujący opiera się na co najmniej jeden z obiektów, którą jest porównywany do zaimplementowania **IComparable** interfejsu. Jest dobrą praktyką, aby zaimplementować **IComparable** na wszystkie klasy są używane jako wartości w kolekcji listy lub kluczy w słowniku kolekcji. Dla ogólnej kolekcji porównania jest określana zgodnie z następujących czynności:  
  
- Jeśli implementacja typu T <xref:System.IComparable%601?displayProperty=nameWithType> jest ogólny interfejs, a następnie domyślny moduł porównujący <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody interfejsu  
  
- Jeśli typ T implementuje niepodstawowy <xref:System.IComparable?displayProperty=nameWithType> interfejsu, a następnie jest domyślna funkcja porównująca <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tego interfejsu.  
  
- Jeśli typ T nie implementuje interfejsu albo, to nie ma żadnych domyślny moduł porównujący i musi być jawnie podana delegat modułu porównującego lub porównywania.  
  
 Aby podać jawne porównanie, niektóre metody akceptują **IComparer** implementacji jako parametr. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda przyjmuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji.  
  
 Bieżące ustawienia kulturowe systemu może wpłynąć na, porównywanie i sortowanie w kolekcji. Domyślnie, porównywania i sortowania w **kolekcje** klasy są zależne od kultury. Aby ignorować ustawienie kultury i dlatego uzyskanie spójnego porównywanie i sortowanie wyników, użyj <xref:System.Globalization.CultureInfo.InvariantCulture%2A> za pomocą przeciążenia składowych, które akceptują <xref:System.Globalization.CultureInfo>. Aby uzyskać więcej informacji, zobacz [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie niezależnych od kultury operacje na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Przykład równości i sortowania  
 Poniższy kod przedstawia implementację <xref:System.IEquatable%601> i <xref:System.IComparable%601> obiektu proste biznesowych. Ponadto, gdy obiekt jest przechowywana na liście i sortowane, zobaczysz że wywołanie <xref:System.Collections.Generic.List%601.Sort> metody powoduje użycie domyślny moduł porównujący dla `Part` typu i <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metody implementowane za pomocą metody anonimowej.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
