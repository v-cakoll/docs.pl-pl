---
title: 'Porady: definiowanie równości wartości dla typu (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#] , overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: c0105371bd39c3999aafca867a7bb7a59fd367c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Porady: definiowanie równości wartości dla typu (Przewodnik programowania w języku C#)
Podczas definiowania klasy lub struktury, możesz zdecydować, czy dobrym rozwiązaniem jest utworzenie niestandardowej definicji równości wartości (lub odpowiednik) dla typu. Zazwyczaj równości wartości zaimplementować w sytuacji, gdy oczekiwano obiektów tego typu do dodania do kolekcji jakieś lub ich podstawowym celem jest przechowywanie zestaw pól lub właściwości. Definicja równości wartości można utworzyć na porównania pól i właściwości w typie lub można utworzyć definicji w podzestawie. Jednak w obu przypadkach, w obu klas i struktur, implementacji należy wykonać pięć gwarancje korelacji:  
  
1.  x.`Equals`(x) zwraca `true.` jest to właściwość zwrotnej.  
  
2.  x.`Equals`(y) zwraca taką samą wartość jak y.`Equals`(x). Jest to właściwość symetrycznego.  
  
3.  Jeśli (x.`Equals`(y) & & y.`Equals`(z)) zwraca `true`, następnie x.`Equals`(z) zwraca `true`. Jest to właściwość przechodnie.  
  
4.  Kolejne wywołania x.`Equals`return (y), tę samą wartość, jak długo obiekty odwołuje się x i y nie są modyfikowane.  
  
5.  x.`Equals`(null) zwraca `false`. Jednak wartości null. Equals(null) zgłasza wyjątek; nie podlega reguły dwa powyżej.  
  
 Wszystkie struktury już definiujących ma domyślną implementację równości wartości, która dziedziczy po jego <xref:System.ValueType?displayProperty=nameWithType> zastąpienie <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. Ta implementacja używa odbicia do sprawdzenia wszystkie pola i właściwości w typie. Ta implementacja tworzy poprawnych wyników, ale jest stosunkowo powolne w porównaniu do niestandardowych implementację, która zapisu specjalnie dla typu.  
  
 Szczegóły implementacji równości wartości są różne dla klas i struktur. Jednak zarówno klas i struktur wymagają te same czynności podstawowe wykonywania równości:  
  
1.  Zastąpienie [wirtualnego](../../../csharp/language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody. W większości przypadków implementacji `bool Equals( object obj )` należy po prostu Wywołaj do określonego typu `Equals` metodę, która jest implementacją <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu. (Zobacz krok 2.)  
  
2.  Implementowanie <xref:System.IEquatable%601?displayProperty=nameWithType> interfejsu, zapewniając określonego typu `Equals` metody. Jest to, gdy wykonywane jest porównanie równoważność rzeczywistych. Na przykład można zdecydować zdefiniować równości, porównując tylko jeden lub dwa pola danego typu. Nie zgłaszają wyjątki od `Equals`. Dla klas tylko: Ta metoda powinna badać tylko pola, które są zadeklarowane w klasie. Powinna wywołać `base.Equals` do pól, które znajdują się w klasie podstawowej. (Nie należy tego robić, jeśli typ dziedziczy bezpośrednio z <xref:System.Object>, ponieważ <xref:System.Object> implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> sprawdza równość odwołania.)  
  
3.  Opcjonalne, ale zalecane: przeciążenia [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) i [! =](../../../csharp/language-reference/operators/not-equal-operator.md) operatorów.  
  
4.  Zastąpienie <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dwa obiekty, które mają taki sam wygenerować równości wartości skrótu.  
  
5.  Opcjonalnie: Aby obsługiwać definicje "większe niż" lub "mniejsze niż", wdrożenie <xref:System.IComparable%601> interfejsu dla danego typu, a także przeciążać [ <= ](../../../csharp/language-reference/operators/less-than-equal-operator.md) i [ >= ](../../../csharp/language-reference/operators/greater-than-equal-operator.md) operatory .  
  
 Pierwszym przykładzie poniżej przedstawia implementację klasy. Drugi przykład przedstawia implementację struktury.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak do zaimplementowania równości wartości w klasie (typ odwołania).  
  
 [!code-csharp[csProgGuideStatements#19](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_1.cs)]  
  
 W klasach (typy referencyjne) Domyślna implementacja obu <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> metody przeprowadza porównanie równości odwołań, nie sprawdzania równości wartości. Gdy implementujący zastępuje metodę wirtualną, ma na celu nadaj wartość semantykę równości.  
  
 `==` i `!=` operatorów można używać z klasami, nawet jeśli klasa nie przeciążać je. Jednak domyślne zachowanie jest sprawdzania równości odwołania. W klasie, jeśli można przeciążać `Equals` metody powinien przeciążać `==` i `!=` operatorów, ale nie jest wymagana.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób wykonania równości wartości w strukturze (typ wartości):  
  
 [!code-csharp[csProgGuideStatements#20](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-define-value-equality-for-a-type_2.cs)]  
  
 Struktur, domyślna implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (czyli zastąpiona wersja w <xref:System.ValueType?displayProperty=nameWithType>) przeprowadza sprawdzanie równości wartości przy użyciu odbicia, aby porównać wartości wszystkich pól w typie. Gdy implementujący zastępuje wirtualnego `Equals` metody w strukturze celem jest zapewnienie bardziej wydajny sposób sprawdzanie równości wartości i, opcjonalnie, na podstawie podzbiór właściwości lub pola struktury.  
  
 [ == ](../../../csharp/language-reference/operators/equality-comparison-operator.md) i [! =](../../../csharp/language-reference/operators/not-equal-operator.md) operatory nie może działać na struktury, chyba że ich overloads jawnie struktury.  
  
## <a name="see-also"></a>Zobacz też  
 [Porównywanie równości](../../../csharp/programming-guide/statements-expressions-operators/equality-comparisons.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
