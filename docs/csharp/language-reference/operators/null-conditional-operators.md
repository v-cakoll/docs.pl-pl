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
# <a name="-and--null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="2e87b-102">?.</span><span class="sxs-lookup"><span data-stu-id="2e87b-102">?.</span></span> <span data-ttu-id="2e87b-103">i? warunkowe null [] operatory (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2e87b-103">and ?[] null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="2e87b-104">Wykorzystywane do testowania dla wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[]`) operacji.</span><span class="sxs-lookup"><span data-stu-id="2e87b-104">Used to test for null before performing a member access (`?.`) or index (`?[]`) operation.</span></span>  <span data-ttu-id="2e87b-105">Tych operatorów pomóc zapisu sprawdza mniej kod obsługujący wartości null, szczególnie w przypadku malejącej do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="2e87b-105">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="2e87b-106">Operatory warunku wartości null są short-circuiting.</span><span class="sxs-lookup"><span data-stu-id="2e87b-106">The null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="2e87b-107">Jeśli jedna operacja w łańcuchu operacji dostępu i indeksu warunkowy element członkowski zwraca wartość null, pozostałe wykonywania łańcucha zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="2e87b-107">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="2e87b-108">W poniższym przykładzie `E` nie jest wykonywana Jeśli `A`, `B`, lub `C` obliczane do wartości null.</span><span class="sxs-lookup"><span data-stu-id="2e87b-108">In the following example, `E` doesn't execute if `A`, `B`, or `C` evaluates to null.</span></span>
  
```csharp
A?.B?.C?.Do(E);
A?.B?.C?[E];
```

```vb
A?.B?.C?.Do(E);
A?.B?.C?(E);
```  
  
 <span data-ttu-id="2e87b-109">Użyj innego dostępu element członkowski warunku wartości null jest powoływanie delegatów w sposób obsługującej wielowątkowość ze znacznie mniejsza ilość kodu.</span><span class="sxs-lookup"><span data-stu-id="2e87b-109">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="2e87b-110">Stary sposób wymaga kodu podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="2e87b-110">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="2e87b-111">Nowy sposób jest znacznie prostsza:</span><span class="sxs-lookup"><span data-stu-id="2e87b-111">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="2e87b-112">Nowy sposób jest bezpieczne wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, zachowania wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="2e87b-112">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="2e87b-113">Należy jawnie wywołać `Invoke` metody ponieważ nie istnieje żadna Składnia wywołania delegata warunkowe null `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="2e87b-113">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="2e87b-114">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="2e87b-114">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="2e87b-115">Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="2e87b-115">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2e87b-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e87b-116">See Also</span></span>  
 [<span data-ttu-id="2e87b-117">?? (operator łączenie null)</span><span class="sxs-lookup"><span data-stu-id="2e87b-117">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="2e87b-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="2e87b-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="2e87b-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2e87b-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="2e87b-120">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e87b-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="2e87b-121">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="2e87b-121">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
