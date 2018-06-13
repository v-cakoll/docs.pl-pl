---
title: Wykonanie lewych sprzężeń zewnętrznych
description: Jak wykonanie lewych sprzężeń zewnętrznych.
ms.date: 12/1/2016
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: aacab1ac6f4ab2c10b393cf0b2c578a13d9b9306
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33284280"
---
# <a name="perform-left-outer-joins"></a>Wykonanie lewych sprzężeń zewnętrznych
Lewe sprzężenie zewnętrzne jest sprzężenia, w której każdy element pierwsza kolekcja jest zwracany, niezależnie od tego, czy ma żadnych elementów skorelowane w druga kolekcja. LINQ umożliwia wykonywanie lewe sprzężenie zewnętrzne, wywołując <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano sposób użycia <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> metody w wynikach sprzężenia grupy, aby wykonać lewe sprzężenie zewnętrzne.  
  
 Pierwszym etapem produkujących lewe sprzężenie zewnętrzne dwóch kolekcji ma wykonywać sprzężenie wewnętrzne za pomocą sprzężenia grupy. (Zobacz [wykonanie sprzężeń wewnętrznych](perform-inner-joins.md) opis tego procesu.) W tym przykładzie lista `Person` obiektów jest wewnętrzny przyłączonych do listy `Pet` obiektów na podstawie `Person` obiektu, który odpowiada `Pet.Owner`.  
  
 Drugim krokiem jest uwzględnienie każdego elementu pierwszej kolekcji (lewych) w zestawie nawet wtedy, gdy ten element nie ma żadnych wyników w kolekcja prawa wyników. Jest to osiągane przez wywołanie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> na poszczególnych sekwencji zgodnych elementów z grupy sprzężenia. W tym przykładzie <xref:System.Linq.Enumerable.DefaultIfEmpty%2A> zostanie wywołany dla poszczególnych sekwencji zgodnych `Pet` obiektów. Metoda zwraca kolekcję, która zawiera pojedynczą, wartość domyślną, jeśli sekwencja zgodnych `Pet` obiektów jest pusta dla żadnego `Person` obiektu, zapewniając, że każdy `Person` obiektu jest reprezentowana w zbiorze wyników.  
  
> [!NOTE]
>  Wartość domyślna dla typu odwołania to `null`; w związku z tym przykładzie wyszukuje odwołanie o wartości null przed uzyskaniem dostępu do każdego elementu `Pet` kolekcji.  
  
 [!code-csharp[CsLINQProgJoining#7](../../../samples/snippets/csharp/concepts/linq/how-to-perform-left-outer-joins_1.cs)]  
 
## <a name="see-also"></a>Zobacz także  
 <xref:System.Linq.Enumerable.Join%2A>  
 <xref:System.Linq.Enumerable.GroupJoin%2A>  
 [Wykonywanie sprzężeń wewnętrznych](perform-inner-joins.md)  
 [Wykonywanie sprzężeń grupowanych](perform-grouped-joins.md)  
 [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  
 
