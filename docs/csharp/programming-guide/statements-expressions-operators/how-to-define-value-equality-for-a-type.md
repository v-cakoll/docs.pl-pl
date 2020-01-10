---
title: Jak zdefiniować równość wartości dla przewodnika C# programowania typu
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 5eb1aaf96097d2c00cb04e24e65e01464f5f00c6
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711977"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Jak zdefiniować równość wartości dla typu (C# Przewodnik programowania)

Podczas definiowania klasy lub struktury należy zdecydować, czy warto utworzyć niestandardową definicję równości (lub równoważności) dla typu. Zazwyczaj należy zaimplementować równość wartości, gdy obiekty typu powinny być dodawane do kolekcji niektórych rodzajów sortowania, lub gdy ich głównym celem jest przechowywanie zestawu pól lub właściwości. Można oprzeć swoją definicję równości wartości na porównaniu wszystkich pól i właściwości w typie lub oprzeć definicję w podzbiorze. Jednak w obu przypadkach i w obu klasach i strukturach implementacja powinna być zgodna z pięcioma gwarancjami równoważności:  
  
1. `x.Equals(x)` zwraca `true`. Jest to nazywane właściwością zwrotną.  
  
2. `x.Equals(y)` zwraca tę samą wartość, co `y.Equals(x)`. Jest to nazywane właściwością symetrycznymi.  
  
3. Jeśli `(x.Equals(y) && y.Equals(z))` zwraca `true`, `x.Equals(z)` zwraca `true`. Jest to nazywane właściwością przechodnią.  
  
4. Kolejne wywołania `x.Equals(y)` zwracają tę samą wartość, o ile obiekty, do których odwołuje się x i y, nie są modyfikowane.  
  
5. `x.Equals(null)` zwraca `false`. Jednak `null.Equals(null)` zgłasza wyjątek; nie przestrzega powyższego numeru reguły.  
  
 Każda zdefiniowana struktura ma już domyślną implementację wartości równość, którą dziedziczy z <xref:System.ValueType?displayProperty=nameWithType> przesłonięcia metody <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. Ta implementacja używa odbicia w celu sprawdzenia wszystkich pól i właściwości w typie. Mimo że ta implementacja daje poprawne wyniki, jest stosunkowo mała w porównaniu z implementacją niestandardową, która jest przeznaczona dla danego typu.  
  
 Szczegóły implementacji dotyczące równości wartości są różne dla klas i struktur. Jednak obie klasy i struktury wymagają tych samych podstawowych kroków w celu wdrożenia równości:  
  
1. Zastąp [wirtualną](../../language-reference/keywords/virtual.md) metodę <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType>. W większości przypadków implementacja `bool Equals( object obj )` powinna tylko wywołać metodę `Equals` specyficzną dla typu, która jest implementacją interfejsu <xref:System.IEquatable%601?displayProperty=nameWithType>. (Zobacz krok 2).  
  
2. Zaimplementuj interfejs <xref:System.IEquatable%601?displayProperty=nameWithType>, dostarczając metodę `Equals` specyficzną dla typu. Jest to miejsce, w którym jest wykonywane rzeczywiste porównanie równoważności. Na przykład można określić równość, porównując tylko jedno lub dwa pola w typie. Nie zgłaszaj wyjątków z `Equals`. Tylko dla klas: Ta metoda powinna analizować tylko pola, które są zadeklarowane w klasie. Powinien wywoływać `base.Equals`, aby przeanalizować pola, które znajdują się w klasie bazowej. (Nie należy tego robić, jeśli typ dziedziczy bezpośrednio z <xref:System.Object>, ponieważ <xref:System.Object> implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> wykonuje kontrolę równości odwołań.)  
  
3. Opcjonalne, ale zalecane: przeciążanie operatorów [==](../../language-reference/operators/equality-operators.md#equality-operator-) i [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) .  
  
4. Przesłoń <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dwa obiekty, które mają równość wartości generowały ten sam kod skrótu.  
  
5. Opcjonalne: aby obsługiwać definicje "większe niż" lub "mniejsze niż", Implementuj interfejs <xref:System.IComparable%601> dla danego typu, a także przeciążać operatory [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) i [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) .  
  
 Pierwszy Poniższy przykład pokazuje implementację klasy. W drugim przykładzie przedstawiono implementację struktury.  

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak zaimplementować równość wartości w klasie (typ referencyjny).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 W przypadku klas (typów referencyjnych) Domyślna implementacja obu metod <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> wykonuje porównanie równości odwołań, a nie sprawdzanie równości wartości. Gdy Realizator zastępuje metodę wirtualną, celem jest przyznanie semantyki równości wartości IT.  
  
 Operatory `==` i `!=` mogą być używane z klasami, nawet jeśli Klasa nie przeciąża ich. Jednak domyślnym zachowaniem jest wykonanie kontroli równości odwołań. W klasie, w przypadku przeciążenia metody `Equals` należy przeciążać operatory `==` i `!=`, ale nie jest to wymagane.  

## <a name="example"></a>Przykład

 Poniższy przykład pokazuje, jak zaimplementować równość wartości w strukturze (typ wartości):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 W przypadku struktur domyślna implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (która jest zastępowaną wersją w <xref:System.ValueType?displayProperty=nameWithType>) wykonuje kontrolę równości wartości przy użyciu odbicia w celu porównania wartości każdego pola w typie. Gdy Realizator zastępuje metodę `Equals` wirtualnej w strukturze, celem jest zapewnienie wydajniejszej kontroli równości wartości i, opcjonalnie, przeprowadzenie porównania w przypadku niektórych podzestawów pól lub właściwości struktury.  
  
 Operatory [==](../../language-reference/operators/equality-operators.md#equality-operator-) i [! =](../../language-reference/operators/equality-operators.md#inequality-operator-) nie mogą działać w strukturze, chyba że struktura jawnie przeciąża je.  
  
## <a name="see-also"></a>Zobacz także

- [Porównania równości](equality-comparisons.md)
- [Przewodnik programowania w języku C#](../index.md)
