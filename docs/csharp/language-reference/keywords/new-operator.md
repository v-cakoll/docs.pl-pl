---
title: new — Operator (odwołanie w C#)
ms.date: 03/15/2018
helpviewer_keywords:
- new operator keyword [C#]
ms.assetid: a212b697-a79b-4105-9923-1f7b108036e8
ms.openlocfilehash: 2ba3c574897ae5f1ec66e3810e23f0af74bd8872
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33268924"
---
# <a name="new-operator-c-reference"></a>new — Operator (odwołanie w C#)
Używany do tworzenia obiektów i wywołania konstruktorów. Na przykład:  
  
```csharp
Class1 obj  = new Class1();  
```  
  
 Służy również do tworzenia wystąpień typów anonimowych:  
  
```csharp
var query = from cust in customers  
            select new { Name = cust.Name, Address = cust.PrimaryAddress };  
```  
  
 `new` Operator również służy do wywoływania domyślnego konstruktora dla typów wartości. Na przykład:  
  
```csharp
int i = new int();  
```  
  
 W powyższych instrukcji `i` jest ustawiana na `0`, która jest wartością domyślną dla typu `int`. Instrukcja ma ten sam efekt w następujący sposób:  
  
```csharp
int i = 0;  
```  
  
 Aby uzyskać pełną listę wartości domyślne, zobacz [tabela wartości domyślnych](../../../csharp/language-reference/keywords/default-values-table.md).  
  
 Należy jednak pamiętać błędu, aby zadeklarować konstruktora domyślnego dla [struktury](../../../csharp/language-reference/keywords/struct.md) ponieważ każdy typ wartości niejawnie ma publicznego konstruktora domyślnego. Można zadeklarować konstruktory sparametryzowane w typie struktury można ustawić wartości początkowej, ale tylko jest to konieczne, jeśli są wymagane wartości innej niż domyślna.  
  
 Zarówno typ wartości obiektów, takich jak struktury, jak i typ referencyjny obiektów, takich jak klasy zostaną zniszczone automatycznie, ale typ wartości obiektów zostaną zniszczone podczas ich zawierającego kontekście zostanie zniszczony, podczas gdy typ referencyjny obiekty zostaną zniszczone w pamięci Moduł zbierający na czas nieokreślony, po usunięciu ostatniego odwołania do nich. Dla typów, które zawierają zasoby, takie jak dojścia do plików lub połączeń sieciowych pożądane jest fragmentów oczyszczania deterministyczna, aby upewnić się, że zasoby, które zawierają są wydawane tak szybko, jak to możliwe. Aby uzyskać więcej informacji, zobacz [za pomocą instrukcji](../../../csharp/language-reference/keywords/using-statement.md).  
  
 `new` Operator nie może być przeciążony.  
  
 Jeśli `new` operator nie może przydzielić pamięci, zgłasza wyjątek, <xref:System.OutOfMemoryException>.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie `struct` utworzenia i zainicjowana przy użyciu obiektu i obiekt klasy `new` operatora, a następnie przypisać wartości. Wartość domyślna i przypisane wartości są wyświetlane.  
  
 [!code-csharp[csrefKeywordsOperator#7](codesnippet/CSharp/new-operator_1.cs)]  
  
 W przykładzie, który jest domyślna wartość ciągu `null`. W związku z tym nie jest wyświetlany.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [Słowa kluczowe operatora](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [new](../../../csharp/language-reference/keywords/new.md)  
 [Typy anonimowe](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
