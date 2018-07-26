---
title: new — Operator (odwołanie w C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39243950"
---
# <a name="new-operator-c-reference"></a>new — Operator (odwołanie w C#)
Używane do tworzenia obiektów i wywoływać konstruktorów. Na przykład:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Służy również do tworzenia wystąpień typów anonimowych:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` Operator jest również używany do wywoływania domyślnego konstruktora dla typów wartości. Na przykład:  
  
```csharp
int i = new int();  
```  
  
 W poprzednich instrukcji `i` jest inicjowany do `0`, która jest wartością domyślną dla typu `int`. Wykonywanie instrukcji ma taki sam skutek jak poniżej:  
  
```csharp
int i = 0;  
```  
  
 Aby uzyskać pełną listę wartości domyślnych, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Należy pamiętać, że jest błąd, aby zadeklarować Konstruktor domyślny dla [struktury](../../../csharp/language-reference/keywords/struct.md) ponieważ każdego typu wartości niejawnie ma publicznego konstruktora domyślnego. Istnieje możliwość zadeklarować konstruktory sparametryzowane w typie struct, można ustawić wartości początkowej, ale tylko jest to konieczne, jeśli wymagane są wartości innej niż domyślna.  
  
 Typ odwołania obiektów, takich jak klasy i obiekty typu wartości, takie jak struktury są niszczone, automatycznie, ale obiekty typu wartości jest niszczony, kiedy ich zawierającego kontekstu jest niszczony, natomiast obiekty typu odwołania są niszczone, wyrzucanie elementów Moduł zbierający na nieokreślony czas, po usunięciu ostatniego odwołania do nich. W przypadku typów, które zawierają zasoby, takie jak dojścia do plików lub połączeń sieciowych pożądane jest mogą wykorzystać deterministyczne cleanup, aby upewnić się, jak najszybciej zwolnienie zasobów, które zawierają. Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).  
  
 Operator `new` nie może być przeciążony.  
  
 Jeśli `new` operator nie może przydzielić pamięci, zgłosi wyjątek, <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `struct` obiektu i obiekt klasy są tworzone i inicjowane za pomocą `new` operatora, a następnie przypisać wartości. Wartość domyślna i przypisane wartości są wyświetlane.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 Zwróć uwagę, w tym przykładzie jest wartością domyślną ciągu `null`. W związku z tym nie jest wyświetlany.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
