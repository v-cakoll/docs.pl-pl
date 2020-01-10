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
ms.openlocfilehash: fc6972061994e17c2176d3ab278b8d2b37c725ee
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711392"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porównywanie i sortowanie w kolekcjach
Klasy <xref:System.Collections> wykonują porównania niemal wszystkich procesów związanych z zarządzaniem kolekcjami, niezależnie od tego, czy są szukane elementy do usunięcia, czy zwracająca wartość pary klucz-wartość.  
  
 Kolekcje zwykle wykorzystują funkcję porównującą równość i/lub funkcję porównującą porządkowania. Dwa konstrukcje są używane do porównywania.  
  
<a name="BKMK_Checkingforequality"></a>   
## <a name="checking-for-equality"></a>Sprawdzanie równości  
 Metody takie jak `Contains`, <xref:System.Collections.IList.IndexOf%2A>, <xref:System.Collections.Generic.List%601.LastIndexOf%2A>i `Remove` wykorzystują funkcję porównującą równość dla elementów kolekcji. Jeśli kolekcja jest ogólna, niż elementy są porównywane pod kątem równości, zgodnie z poniższymi wskazówkami:  
  
- Jeśli typ T implementuje interfejs ogólny <xref:System.IEquatable%601>, wówczas funkcja porównująca równość jest metodą <xref:System.IEquatable%601.Equals%2A> tego interfejsu.  
  
- Jeśli typ T nie implementuje <xref:System.IEquatable%601>, używany jest <xref:System.Object.Equals%2A?displayProperty=nameWithType>.  
  
 Ponadto niektóre przeciążenia konstruktorów dla kolekcji słowników akceptują implementację <xref:System.Collections.Generic.IEqualityComparer%601>, która jest używana do porównywania kluczy pod kątem równości. Aby zapoznać się z przykładem, zapoznaj się z konstruktorem <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType>.  
  
<a name="BKMK_Determiningsortorder"></a>   
## <a name="determining-sort-order"></a>Określanie kolejności sortowania  
 Metody, takie jak `BinarySearch` i `Sort`, wykorzystują funkcję porównującą porządkowanie dla elementów kolekcji. Porównania mogą znajdować się między elementami kolekcji lub między elementem a określoną wartością. W przypadku porównywania obiektów istnieje koncepcja `default comparer` i `explicit comparer`.  
  
 Domyślna funkcja porównująca polega na co najmniej jednym z obiektów, które są porównywane w celu zaimplementowania interfejsu **IComparable** . Dobrym sposobem implementacji interfejsu **IComparable** dla wszystkich klas są używane jako wartości w kolekcji list lub klucze w kolekcji słowników. W przypadku kolekcji ogólnej Porównywanie równości jest określane na podstawie następujących elementów:  
  
- Jeśli typ T implementuje interfejs ogólny <xref:System.IComparable%601?displayProperty=nameWithType>, wówczas domyślną metodą porównującą jest metoda <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> tego interfejsu  
  
- Jeśli typ T implementuje interfejs nieogólny <xref:System.IComparable?displayProperty=nameWithType>, wówczas domyślną metodą porównującą jest metoda <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> tego interfejsu.  
  
- Jeśli typ T nie implementuje interfejsu, wówczas nie ma domyślnego programu porównującego i należy jawnie podać delegata lub delegowanie porównania.  
  
 Aby zapewnić jawne porównania, niektóre metody akceptują implementację **IComparer** jako parametr. Na przykład Metoda <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> akceptuje implementację <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType>.  
  
 Bieżące ustawienie kultury systemu może wpływać na porównania i sortować je w obrębie kolekcji. Domyślnie porównania i sortowania w klasach **kolekcji** są zależne od kultury. Aby zignorować ustawienie kultury i w związku z tym uzyskać spójne wyniki porównania i sortowania, użyj <xref:System.Globalization.CultureInfo.InvariantCulture%2A> z przeciążeniami elementów członkowskich, które akceptują <xref:System.Globalization.CultureInfo>. Aby uzyskać więcej informacji, zobacz [wykonywanie operacji na ciągach bez uwzględniania kultur w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie operacji na ciągach nieuwzględniających kulturę w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>   
## <a name="equality-and-sort-example"></a>Przykład równości i sortowania  
 Poniższy kod ilustruje implementację <xref:System.IEquatable%601> i <xref:System.IComparable%601> na prostym obiekcie biznesowym. Ponadto, gdy obiekt jest przechowywany na liście i posortowany, zobaczysz, że wywołanie metody <xref:System.Collections.Generic.List%601.Sort> powoduje użycie domyślnej funkcji porównującej dla typu `Part`, a metoda <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> zaimplementowana przy użyciu metody anonimowej.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
