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
ms.openlocfilehash: 3360652f22ed39ccfd99f9863052fe584b78562f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78159263"
---
# <a name="comparisons-and-sorts-within-collections"></a>Porównywanie i sortowanie w kolekcjach
Klasy <xref:System.Collections> wykonywać porównania w prawie wszystkich procesów związanych z zarządzaniem kolekcji, czy wyszukiwanie elementu, aby usunąć lub zwracanie wartości pary klucz i wartość.  
  
 Kolekcje zazwyczaj wykorzystują porównywarka równości i/lub konektor porównujący. Dwie konstrukcje są używane do porównań.  
  
<a name="BKMK_Checkingforequality"></a>
## <a name="checking-for-equality"></a>Sprawdzanie równości  
 Metody, takie `Contains` <xref:System.Collections.IList.IndexOf%2A>jak <xref:System.Collections.Generic.List%601.LastIndexOf%2A>, `Remove` , i użyć porównania równości dla elementów kolekcji. Jeśli kolekcja jest ogólny, niż elementy są porównywane do równości zgodnie z następującymi wytycznymi:  
  
- Jeśli typ T <xref:System.IEquatable%601> implementuje interfejs ogólny, moduł <xref:System.IEquatable%601.Equals%2A> porównujący równość jest metodą tego interfejsu.  
  
- Jeśli typ T <xref:System.IEquatable%601>nie <xref:System.Object.Equals%2A?displayProperty=nameWithType> implementuje , jest używany.  
  
 Ponadto niektóre przeciążenia konstruktora dla <xref:System.Collections.Generic.IEqualityComparer%601> kolekcji słownika zaakceptować implementację, która służy do porównywania kluczy równości. Na przykład zobacz <xref:System.Collections.Generic.Dictionary%602.%23ctor%2A?displayProperty=nameWithType> konstruktora.  
  
<a name="BKMK_Determiningsortorder"></a>
## <a name="determining-sort-order"></a>Określanie kolejności sortowania  
 Metody, takie `BinarySearch` `Sort` jak i używać konektor dla elementów kolekcji. Porównania mogą być między elementami kolekcji lub między elementem i określoną wartością. Do porównywania obiektów istnieje pojęcie `default comparer` a `explicit comparer`i .  
  
 Domyślny moduł porównujący opiera się na co najmniej jednym z obiektów porównywanych do zaimplementowania interfejsu **IComparable.** Jest dobrym rozwiązaniem, aby zaimplementować **IComparable** na wszystkich klasach są używane jako wartości w kolekcji listy lub jako klucze w kolekcji słownika. Dla kolekcji ogólnej porównanie równości jest określane zgodnie z następującymi czynnościami:  
  
- Jeśli typ T <xref:System.IComparable%601?displayProperty=nameWithType> implementuje interfejs ogólny, domyślnym <xref:System.IComparable%601.CompareTo%28%600%29?displayProperty=nameWithType> modułem porównującym jest metoda tego interfejsu  
  
- Jeśli typ T implementuje <xref:System.IComparable?displayProperty=nameWithType> interfejs nierodzajowy, domyślnym <xref:System.IComparable.CompareTo%28System.Object%29?displayProperty=nameWithType> modułem porównującym jest metoda tego interfejsu.  
  
- Jeśli typ T nie implementuje żadnego z interfejsów, nie ma domyślnego modułu porównującego, a moduł porównujący lub delegat porównania musi być jawnie podany.  
  
 Aby zapewnić jawne porównania, niektóre metody akceptują implementację **IComparer** jako parametr. Na przykład <xref:System.Collections.Generic.List%601.Sort%2A?displayProperty=nameWithType> metoda akceptuje <xref:System.Collections.Generic.IComparer%601?displayProperty=nameWithType> implementację.  
  
 Bieżące ustawienie kultury systemu może mieć wpływ na porównania i sortuje w kolekcji. Domyślnie porównania i sortowania w **kolekcje** klas są zależne od kultury. Aby zignorować ustawienie kultury i w związku z <xref:System.Globalization.CultureInfo.InvariantCulture%2A> tym uzyskać spójne wyniki <xref:System.Globalization.CultureInfo>porównania i sortowania, należy użyć z przeciążenia elementu członkowskiego, które akceptują . Aby uzyskać więcej informacji, zobacz [Wykonywanie operacji ciągów niewrażliwych na kulturę w kolekcjach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) i [wykonywanie operacji ciągów niewrażliwych na kulturę w tablicach](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md).  
  
<a name="BKMK_Equalityandsortexample"></a>
## <a name="equality-and-sort-example"></a>Przykład równości i sortowania  
 Poniższy kod demonstruje <xref:System.IEquatable%601> implementację i <xref:System.IComparable%601> na prosty obiekt biznesowy. Ponadto gdy obiekt jest przechowywany na liście i posortowane, <xref:System.Collections.Generic.List%601.Sort> zobaczysz, że wywołanie metody powoduje `Part` użycie domyślnego porównania dla typu i <xref:System.Collections.Generic.List%601.Sort%28System.Comparison%7B%600%7D%29> metody zaimplementowanej przy użyciu metody anonimowej.  
  
 [!code-csharp[System.Collections.Generic.List.Sort#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.collections.generic.list.sort/cs/program.cs#1)]
 [!code-vb[System.Collections.Generic.List.Sort#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.collections.generic.list.sort/vb/module1.vb#1)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Collections.IComparer>
- <xref:System.IEquatable%601>
- <xref:System.Collections.Generic.IComparer%601>
- <xref:System.IComparable>
- <xref:System.IComparable%601>
