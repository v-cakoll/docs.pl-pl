---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 04/03/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- null-conditional operators [C#]
- null-conditional operators [Visual Basic]
- ?. operator [C#]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
ms.openlocfilehash: f00d5e489931d9c1172a21ee5f0d3e3d0a6f4a4e
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44132230"
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="b652a-102">?.</span><span class="sxs-lookup"><span data-stu-id="b652a-102">?.</span></span> <span data-ttu-id="b652a-103">Operatory warunkowe null ?. oraz ? [] (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b652a-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="b652a-104">Testuje, czy wartość lewego argumentu operacji to „null”, zanim przeprowadzi operację dostępu do elementu (`?.`) lub indeksowania (`?[]`). Zwraca `null`, jeśli wartość lewego argumentu operacji to `null`.</span><span class="sxs-lookup"><span data-stu-id="b652a-104">Tests the value of the left-hand operand for null before performing a member access (`?.`) or index (`?[]`) operation; returns `null` if the left-hand operand evaluates to `null`.</span></span> 

<span data-ttu-id="b652a-105">Operatory te pomagają ograniczyć ilość kodu potrzebnego do sprawdzenia wystąpień wartości „null”, zwłaszcza w przypadku wchodzenia głębiej w struktury danych.</span><span class="sxs-lookup"><span data-stu-id="b652a-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
```csharp  
int? length = customers?.Length; // null if customers is null   
Customer first = customers?[0];  // null if customers is null  
int? count = customers?[0]?.Orders?.Count();  // null if customers, the first customer, or Orders is null  
```  
  
```vb  
Dim length = customers?.Length  ' null if customers is null  
Dim first as Customer = customers?(0)  ' null if customers is null  
Dim count as Integer? = customers?(0)?.Orders?.Count()  ' null if customers, the first customer, or Orders is null  
```  
  
 <span data-ttu-id="b652a-106">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="b652a-106">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="b652a-107">Jeśli jedna z operacji w łańcuchu zwraca wartość `null`, dalsze wykonanie łańcucha zostaje przerwane.</span><span class="sxs-lookup"><span data-stu-id="b652a-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="b652a-108">W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość `null`.</span><span class="sxs-lookup"><span data-stu-id="b652a-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="b652a-109">Inne zastosowanie dostępu do elementu członkowskiego przy użyciu operatora warunkowego `null` polega na wywołaniu delegatów w sposób bezpieczny wątkowo i ze znacznie mniejszą ilością kodu.</span><span class="sxs-lookup"><span data-stu-id="b652a-109">Another use for the null-conditional member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="b652a-110">Stary sposób wymaga kodu podobnego do poniższego:</span><span class="sxs-lookup"><span data-stu-id="b652a-110">The old way requires code like the following:</span></span>  
  
```csharp  
var handler = this.PropertyChanged;  
if (handler != null)  
    handler(…);
```  
  
```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```  
  
 <span data-ttu-id="b652a-111">Nowy sposób jest znacznie prostszy:</span><span class="sxs-lookup"><span data-stu-id="b652a-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(…)  
```  

```vb
PropertyChanged?.Invoke(…)
```  
  
 <span data-ttu-id="b652a-112">Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="b652a-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="b652a-113">Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.</span><span class="sxs-lookup"><span data-stu-id="b652a-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="b652a-114">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="b652a-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="b652a-115">Aby uzyskać więcej informacji, zobacz [odwołanie językowe Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="b652a-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b652a-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b652a-116">See Also</span></span>

- [<span data-ttu-id="b652a-117">?? (z operatorem łączenia wartości null)</span><span class="sxs-lookup"><span data-stu-id="b652a-117">?? (null-coalescing operator)</span></span>](null-coalescing-operator.md)  
- [<span data-ttu-id="b652a-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="b652a-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b652a-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b652a-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b652a-120">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b652a-120">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
