---
title: Jak zdefiniować równość wartości dla typu - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- overriding Equals method [C#]
- object equivalence [C#]
- Equals method [C#], overriding
- value equality [C#]
- equivalence [C#]
ms.assetid: 4084581e-b931-498b-9534-cf7ef5b68690
ms.openlocfilehash: 140be18698a40be8f394b31fcd42b97d6685cb98
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157094"
---
# <a name="how-to-define-value-equality-for-a-type-c-programming-guide"></a>Jak zdefiniować równość wartości dla typu (Przewodnik programowania C#)

Podczas definiowania klasy lub struktury, należy zdecydować, czy ma sens, aby utworzyć niestandardową definicję równości wartości (lub równoważności) dla typu. Zazwyczaj należy zaimplementować równość wartości, gdy obiekty tego typu mają zostać dodane do kolekcji pewnego rodzaju lub gdy ich głównym celem jest przechowywanie zestawu pól lub właściwości. Definicję równości wartości można oprzeć na porównaniu wszystkich pól i właściwości w typie lub oprzeć definicję na podzbiorze.

W obu przypadkach i w obu klasach i strukturach implementacja powinna być zgodna z pięcioma `x` `y` gwarancjami równoważności (W przypadku poniższych reguł załóżmy, że , i `z` nie są null):  
  
1. `x.Equals(x)`zwraca `true`. Nazywa się to właściwością refleksyjny.  
  
2. `x.Equals(y)`zwraca tę samą wartość co `y.Equals(x)`. Jest to nazywane właściwością symetryczną.  
  
3. jeśli `(x.Equals(y) && y.Equals(z))` `true`powróci `x.Equals(z)` , `true`a następnie zwraca . Jest to nazywane właściwością przechodnią.  
  
4. Kolejne wywołania `x.Equals(y)` zwracania tej samej wartości, o ile obiekty, do których odwołują się x i y, nie są modyfikowane.  
  
5. Każda wartość nienull nie jest równa null. Jednak CLR sprawdza null na wszystkie wywołania `NullReferenceException` metody `this` i zgłasza, jeśli odwołanie będzie null. W `x.Equals(y)` związku z tym `x` zgłasza wyjątek, gdy jest null. To łamie zasady 1 lub 2, `Equals`w zależności od argumentu .

 Każda struktura, która zostanie zdefiniowana, ma już domyślną <xref:System.ValueType?displayProperty=nameWithType> implementację <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> równości wartości, która dziedziczy po zastąpieniu metody. Ta implementacja używa odbicia, aby zbadać wszystkie pola i właściwości w typie. Mimo że ta implementacja daje poprawne wyniki, jest stosunkowo powolny w porównaniu do implementacji niestandardowej, które można napisać specjalnie dla typu.  
  
 Szczegóły implementacji równości wartości są różne dla klas i struktur. Jednak zarówno klasy, jak i struktury wymagają tych samych podstawowych kroków w celu wdrożenia równości:  
  
1. Zastąp metodę [wirtualną.](../../language-reference/keywords/virtual.md) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> W większości przypadków implementacji `bool Equals( object obj )` należy po prostu `Equals` wywołać metodę specyficzne <xref:System.IEquatable%601?displayProperty=nameWithType> dla typu, która jest implementacja interfejsu. (Patrz krok 2.)  
  
2. Zaimplementuj <xref:System.IEquatable%601?displayProperty=nameWithType> interfejs, udostępniając `Equals` metodę specyficzną dla typu. To jest, gdy rzeczywiste porównanie równoważności jest wykonywana. Na przykład można zdefiniować równość, porównując tylko jedno lub dwa pola w typie. Nie zgłaszaj wyjątków od `Equals`. Tylko dla klas: Ta metoda powinna sprawdzać tylko pola, które są zadeklarowane w klasie. Należy wywołać, `base.Equals` aby zbadać pola, które znajdują się w klasie podstawowej. (Nie należy tego robić, jeśli <xref:System.Object>typ dziedziczy bezpośrednio z , ponieważ <xref:System.Object> implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> wykonuje sprawdzanie równości odwołania.)  
  
3. Opcjonalnie, ale zalecane: [==](../../language-reference/operators/equality-operators.md#equality-operator-) Przeciążenie i [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) operatorów.  
  
4. Zastąp <xref:System.Object.GetHashCode%2A?displayProperty=nameWithType> tak, aby dwa obiekty, które mają równość wartości, wytwarzają ten sam kod skrótu.  
  
5. Opcjonalnie: aby obsługiwać definicje "większe niż" lub <xref:System.IComparable%601> "mniej niż", zaimplementuj interfejs dla swojego typu, a także przeciążają [<=](../../language-reference/operators/comparison-operators.md#less-than-or-equal-operator-) i [>=](../../language-reference/operators/comparison-operators.md#greater-than-or-equal-operator-) operatorów.  
  
 Pierwszy przykład, który następuje pokazuje implementacji klasy. Drugi przykład pokazuje implementacji struktury.  

## <a name="example"></a>Przykład

 W poniższym przykładzie pokazano, jak zaimplementować równość wartości w klasie (typ odwołania).  
  
 [!code-csharp[csProgGuideStatements#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#19)]  
  
 W klasach (typy odwołań) <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> domyślna implementacja obu metod wykonuje porównanie równości odwołania, a nie sprawdzanie równości wartości. Gdy realizator zastępuje metodę wirtualną, celem jest nadanie mu semantyki równości wartości.  
  
 I `==` `!=` operatory mogą być używane z klas, nawet jeśli klasa nie przeciąża ć je. Jednak zachowanie domyślne jest do wykonywania sprawdzania równości odwołania. W klasie, jeśli przeciążenia `Equals` metody, należy `==` przeciążać i `!=` operatorów, ale nie jest wymagane.  

## <a name="example"></a>Przykład

 W poniższym przykładzie pokazano, jak zaimplementować równość wartości w strukturze (typ wartości):  
  
 [!code-csharp[csProgGuideStatements#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideStatements/CS/Statements.cs#20)]  
  
 Dla struktur domyślna implementacja <xref:System.Object.Equals%28System.Object%29?displayProperty=nameWithType> (która jest zastąpiona wersja w) <xref:System.ValueType?displayProperty=nameWithType>wykonuje sprawdzanie równości wartości przy użyciu odbicia do porównania wartości każdego pola w typie. Gdy realizator zastępuje `Equals` metodę wirtualną w strukturze, celem jest zapewnienie bardziej efektywnego sposobu wykonywania sprawdzania równości wartości i opcjonalnie oparcie porównania na niektórych podzbiorach pola lub właściwości struktury.  
  
 Operatory [==](../../language-reference/operators/equality-operators.md#equality-operator-) i [!=](../../language-reference/operators/equality-operators.md#inequality-operator-) nie mogą działać na strukturze, chyba że struktura jawnie je przeciąża.  
  
## <a name="see-also"></a>Zobacz też

- [Porównywanie równości](equality-comparisons.md)
- [Przewodnik programowania w języku C#](../index.md)
