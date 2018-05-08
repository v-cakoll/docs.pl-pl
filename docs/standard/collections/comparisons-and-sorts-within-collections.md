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
ms.openlocfilehash: 11393f4013a1b5ed9dc90154f289466432102a38
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="comparisons-and-sorts-within-collections"></a>Porównywanie i sortowanie w kolekcjach
<xref:System.Collections> Klasy wykonywać porównania w niemal wszystkich procesów Zarządzanie kolekcjami, czy wyszukiwanie elementu do usunięcia lub zwrócenie wartości parę klucza i wartości.  
  
 Kolekcje wykorzystywać zwykle porównania równości i/lub porównania porządkowania. Konstrukcje dwóch służą do porównania.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Sprawdzanie pod kątem równości  
 Metody, takie jak `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, i `Remove` Użyj porównania równości dla elementów kolekcji. Jeśli kolekcja jest ogólny, niż elementy są porównywane pod kątem równości, zgodnie z poniższymi wytycznymi:  
  
-   Jeśli implementuje typu T <xref:System.IEquatable%601> jest ogólny interfejs, a następnie porównania równości <xref:System.IEquatable%601.Equals%2A> metody tego interfejsu.  
  
-   Jeśli typ T nie implementuje <xref:System.IEquatable%601>, <xref:System.Object.Equals%2A?displayProperty=nameWithType> jest używany.  
  
 Ponadto niektóre przeładowania konstruktora dla kolekcji słownika zaakceptować <xref:System.Collections.Generic.IEqualityComparer%601> wdrożenia, który służy do porównywania klucze pod kątem równości. Na przykład zobacz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktora.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Określanie kolejności sortowania  
 Metody, takie jak `BinarySearch` i `Sort` Użyj porównania porządkowania elementów kolekcji. Porównanie może być między elementy kolekcji lub elementu i określoną wartość. Porównanie obiektów, istnieje pojęcie `default comparer` i `explicit comparer`.  
  
 Domyślna funkcja porównująca opiera się na co najmniej jeden z obiektów są porównywane w celu zaimplementowania **IComparable** interfejsu. Dobrym rozwiązaniem do zaimplementowania jest **IComparable** na wszystkie klasy są używane jako wartości w kolekcji list lub kluczy w słowniku kolekcji. Do kolekcji uniwersalnej porównania równości określa się zgodnie z następujących czynności:  
  
-   Jeśli implementuje typu T <xref:System.IComparable%601?displayProperty=nameWithType> jest ogólny interfejs, a następnie domyślna funkcja porównująca <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> metody interfejsu  
  
-   Jeśli typ T implementuje nieogólnego <xref:System.IComparable?displayProperty=nameWithType> interfejsu, a następnie jest domyślna funkcja porównująca <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> metody tego interfejsu.  
  
-   Jeśli typ T nie implementuje interfejsu albo, to nie ma żadnych domyślna funkcja porównująca i podać jawnie delegata porównania lub porównania.  
  
 Aby podać jawne porównań, Zaakceptuj niektóre metody **IComparer** implementacji jako parametr. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda przyjmuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementacji.  
  
 Bieżące ustawienia kulturowe systemu może mieć wpływ na porównywanie i sortowanie w kolekcji. Domyślnie porównywanie i sortowanie w **kolekcje** klasy są zależne od kultury. Ignoruj ustawienia kulturowe i w związku z tym uzyskanie spójnej porównywanie i sortowanie wyników, należy użyć <xref:System.Globalization.CultureInfo.InvariantCulture%2A> z przeciążeń elementu członkowskiego, które akceptują <xref:System.Globalization.CultureInfo>. Aby uzyskać więcej informacji, zobacz [wykonywanie niezależnych od kultury operacje na ciągach w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie niezależnych od kultury operacje na ciągach w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Przykład równości i sortowanie  
 Poniższy kod przedstawia implementację <xref:System.IEquatable%601> i <xref:System.IComparable%601> na obiekt biznesowy proste. Ponadto, gdy obiekt jest przechowywany w postaci listy i sortowane, zobaczysz tego wywołania <xref:System.Collections.Generic.List%601.Sort> metoda powoduje użycie domyślna funkcja porównująca dla `Part` typu i <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metody implementowane za pomocą metody anonimowej.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Collections.IComparer>  
 <xref:System.IEquatable%601>  
 <xref:System.Collections.Generic.IComparer%601>  
 <xref:System.IComparable>  
 <xref:System.IComparable%601>
