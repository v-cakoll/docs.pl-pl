---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 04/03/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
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
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 3ffeaa3c2088d0bb2c000704cfe312b0f9453b68
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="b3ae6-102">?.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-102">?.</span></span> <span data-ttu-id="b3ae6-103">Operatory warunkowe null ?. oraz ? [] (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b3ae6-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="b3ae6-104">Wykorzystywane do testowania wystąpienia wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub odwołaniem do indeksu (`?[]`).</span><span class="sxs-lookup"><span data-stu-id="b3ae6-104">Used to test for null before performing a member access (`?.`) or index (`?[]`) operation.</span></span>  <span data-ttu-id="b3ae6-105">Pomagają one w ograniczeniu ilości kodu potrzebnego do sprawdzenia wystąpień wartości null, zwłaszcza dla przypadków zstępujących do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="b3ae6-106">Operatory warunkowe wartości null są krótkoobiegowe.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-106">The null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="b3ae6-107">Jeśli jedna z operacji w łańcuchu dostępu zwraca wartość null, dalsze wykonanie łańcucha zostaje przerwane.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="b3ae6-108">W poniższym przykładzie `E` nie jest wykonywane, jeśli `A`, `B` lub `C` zwraca wartość null.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="b3ae6-109">Inne użycie operatorów warunkowych null polega na „wątkowo bezpiecznym” wywołaniu delegatów z mniejszą ilością kodu. </span><span class="sxs-lookup"><span data-stu-id="b3ae6-109">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="b3ae6-110">Stary sposób wymaga kodu podobnego do poniższego:</span><span class="sxs-lookup"><span data-stu-id="b3ae6-110">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="b3ae6-111">Nowy sposób jest znacznie prostszy:</span><span class="sxs-lookup"><span data-stu-id="b3ae6-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="b3ae6-112">Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, przechowując wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="b3ae6-113">Należy jawnie wywołać metodę `Invoke`, ponieważ nie istnieje możliwość wywołania delegata warunkowego null za pomocą żadnej z dostępnych składni `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="b3ae6-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="b3ae6-114">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="b3ae6-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="b3ae6-115">Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="b3ae6-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3ae6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b3ae6-116">See Also</span></span>  
 [<span data-ttu-id="b3ae6-117">?? (operator łączenie null)</span><span class="sxs-lookup"><span data-stu-id="b3ae6-117">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="b3ae6-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="b3ae6-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="b3ae6-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="b3ae6-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="b3ae6-120">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3ae6-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="b3ae6-121">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b3ae6-121">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
