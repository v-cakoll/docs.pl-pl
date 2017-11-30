---
title: "Wykonanie lewych sprzężeń zewnętrznych"
description: "Jak wykonanie lewych sprzężeń zewnętrznych."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: f542cee6-3169-4dcf-a631-3a6a79ccd473
ms.openlocfilehash: 0c28c85bf933a411403aefcb91801d28fe1c268e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Wykonanie sprzężeń wewnętrznych](perform-inner-joins.md)  
 [Wykonanie sprzężeń grupowanych](perform-grouped-joins.md)  
 [Typy anonimowe](../programming-guide/classes-and-structs/anonymous-types.md)  
 
