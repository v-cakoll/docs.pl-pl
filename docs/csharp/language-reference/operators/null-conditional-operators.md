---
title: Operatory warunkowe null (C# i Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 9c7b2c8f-a785-44ca-836c-407bfb6d27f5
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c95b4079cf4e71c0ef9cd436ec230337f512229a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="null-conditional-operators-c-and-visual-basic"></a><span data-ttu-id="27e4e-102">Operatory warunkowe null (C# i Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="27e4e-102">Null-conditional Operators (C# and Visual Basic)</span></span>
<span data-ttu-id="27e4e-103">Wykorzystywane do testowania dla wartości null przed wykonaniem dostępu elementu członkowskiego (`?.`) lub indeks (`?[`) operacji.</span><span class="sxs-lookup"><span data-stu-id="27e4e-103">Used to test for null before performing a member access (`?.`) or index (`?[`) operation.</span></span>  <span data-ttu-id="27e4e-104">Tych operatorów pomóc zapisu sprawdza mniej kod obsługujący wartości null, szczególnie w przypadku malejącej do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="27e4e-104">These operators help you write less code to handle null checks, especially for descending into data structures.</span></span>  
  
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
  
 <span data-ttu-id="27e4e-105">W ostatnim przykładzie pokazano, czy short-circuiting operatory warunku wartości null.</span><span class="sxs-lookup"><span data-stu-id="27e4e-105">The last example demonstrates that the null-condition operators are short-circuiting.</span></span>  <span data-ttu-id="27e4e-106">Jeśli jedna operacja w łańcuchu operacji dostępu i indeksu warunkowy element członkowski zwraca wartość null, pozostałe wykonywania łańcucha zatrzymuje.</span><span class="sxs-lookup"><span data-stu-id="27e4e-106">If one operation in a chain of conditional member access and index operation returns null, then the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="27e4e-107">Nadal innych operacji o niższym priorytecie w wyrażeniu.</span><span class="sxs-lookup"><span data-stu-id="27e4e-107">Other operations with lower precedence in the expression continue.</span></span>  <span data-ttu-id="27e4e-108">Na przykład `E` poniżej wykonuje w drugim wierszu i `??` i `==` wykonania operacji.</span><span class="sxs-lookup"><span data-stu-id="27e4e-108">For example, `E` in the following executes in the second line, and the `??` and `==` operations execute.</span></span>  <span data-ttu-id="27e4e-109">W pierwszym wierszu `??` krótkiej obwody i `E` nie wykonuj po lewej ocenia się na inną niż null.</span><span class="sxs-lookup"><span data-stu-id="27e4e-109">In the first line, the `??` short circuits and `E` does not execute when the left side evaluates to non-null.</span></span>
  
```csharp
A?.B?.C?[0] ?? E  
A?.B?.C?[0] == E  
```

```vb
A?.B?.C?(0) ?? E  
A?.B?.C?(0) == E  
```  
  
 <span data-ttu-id="27e4e-110">Użyj innego dostępu element członkowski warunku wartości null jest powoływanie delegatów w sposób obsługującej wielowątkowość ze znacznie mniejsza ilość kodu.</span><span class="sxs-lookup"><span data-stu-id="27e4e-110">Another use for the null-condition member access is invoking delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="27e4e-111">Stary sposób wymaga kodu podobne do poniższych:</span><span class="sxs-lookup"><span data-stu-id="27e4e-111">The old way requires code like the following:</span></span>  
  
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
  
 <span data-ttu-id="27e4e-112">Nowy sposób jest znacznie prostsza:</span><span class="sxs-lookup"><span data-stu-id="27e4e-112">The new way is much simpler:</span></span>  
  
```csharp
PropertyChanged?.Invoke(e)  
```  

```vb
PropertyChanged?.Invoke(e)
```  
  
 <span data-ttu-id="27e4e-113">Nowy sposób jest bezpieczne wątkowo, ponieważ kompilator generuje kod, aby ocenić `PropertyChanged` tylko jeden raz, zachowania wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="27e4e-113">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span>  
  
 <span data-ttu-id="27e4e-114">Należy jawnie wywołać `Invoke` metody ponieważ nie istnieje żadna Składnia wywołania delegata warunkowe null `PropertyChanged?(e)`.</span><span class="sxs-lookup"><span data-stu-id="27e4e-114">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  <span data-ttu-id="27e4e-115">Znaleziono zbyt wiele niejednoznaczne analizy sytuacji, aby umożliwić jego.</span><span class="sxs-lookup"><span data-stu-id="27e4e-115">There were too many ambiguous parsing situations to allow it.</span></span>  
  
## <a name="language-specifications"></a><span data-ttu-id="27e4e-116">Specyfikacje języka</span><span class="sxs-lookup"><span data-stu-id="27e4e-116">Language Specifications</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
 <span data-ttu-id="27e4e-117">Aby uzyskać więcej informacji, zobacz [dokumentacja języka Visual Basic](../../../visual-basic/language-reference/index.md).</span><span class="sxs-lookup"><span data-stu-id="27e4e-117">For more information, see the [Visual Basic Language Reference](../../../visual-basic/language-reference/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27e4e-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="27e4e-118">See Also</span></span>  
 [<span data-ttu-id="27e4e-119">?? (operator łączenie null)</span><span class="sxs-lookup"><span data-stu-id="27e4e-119">?? (null-coalescing operator)</span></span>](null-conditional-operator.md)  
 [<span data-ttu-id="27e4e-120">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="27e4e-120">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="27e4e-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="27e4e-121">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27e4e-122">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27e4e-122">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
 [<span data-ttu-id="27e4e-123">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="27e4e-123">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
