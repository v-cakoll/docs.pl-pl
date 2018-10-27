---
title: Operatory warunkowe null (Visual Basic)
ms.date: 10/19/2018
helpviewer_keywords:
- null-conditional operators [Visual Basic]
- ?. operator [Visual Basic]
- ?[] operator [C#]
- ?[] operator [Visual Basic]
ms.openlocfilehash: c29362a1e335e18b66821919e266b1ce57774692
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195980"
---
# <a name="-and--null-conditional-operators-visual-basic"></a><span data-ttu-id="93cf8-102">?.</span><span class="sxs-lookup"><span data-stu-id="93cf8-102">?.</span></span> <span data-ttu-id="93cf8-103">i? Operatory warunkowe null () (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93cf8-103">and ?() null-conditional operators (Visual Basic)</span></span>

<span data-ttu-id="93cf8-104">Sprawdza wartość operandu po lewej stronie w przypadku wartości null (`Nothing`) przed wykonaniem dostęp do elementu członkowskiego (`?.`) lub indeksu (`?()`) operacja; zwraca `Nothing` Jeśli po lewej stronie operand ma wartość `Nothing`.</span><span class="sxs-lookup"><span data-stu-id="93cf8-104">Tests the value of the left-hand operand for null (`Nothing`) before performing a member access (`?.`) or index (`?()`) operation; returns `Nothing` if the left-hand operand evaluates to `Nothing`.</span></span> <span data-ttu-id="93cf8-105">Należy pamiętać, że w wyrażeniach, które zazwyczaj zwróci typów wartości, operatorów warunkowych działających z wartością null zwraca <xref:System.Nullable%601>.</span><span class="sxs-lookup"><span data-stu-id="93cf8-105">Note that, in the expressions that would ordinarily return value types, the null-conditional operator returns a <xref:System.Nullable%601>.</span></span>

<span data-ttu-id="93cf8-106">Te operatory pomóc w pisaniu mniejszej ilości kodu do obsługi sprawdzanie wartości null, szczególnie w przypadku, gdy malejąco do struktur danych.</span><span class="sxs-lookup"><span data-stu-id="93cf8-106">These operators help you write less code to handle null checks, especially when descending into data structures.</span></span> <span data-ttu-id="93cf8-107">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="93cf8-107">For example:</span></span>

```vb
Dim length As Integer? = customers?.Length  ' Nothing if customers is Nothing  
Dim first As Customer = customers?(0)  ' Nothing if customers is Nothing  
Dim count As Integer? = customers?(0)?.Orders?.Count()  ' Nothing if customers, the first customer, or Orders is Nothing  
```

<span data-ttu-id="93cf8-108">Dla porównania alternatywnych kod dla pierwszego dnia te wyrażenia bez operatorów warunkowych działających z wartością null jest:</span><span class="sxs-lookup"><span data-stu-id="93cf8-108">For comparison, the alternative code for the first of these expressions without a null-conditional operator is:</span></span>

```vb
Dim length As Integer
If customers IsNot Nothing Then
   length = customers.Length
End If
```

<span data-ttu-id="93cf8-109">Operatory warunkowe `null` skracają łańcuch wykonywania operacji.</span><span class="sxs-lookup"><span data-stu-id="93cf8-109">The null-conditional operators are short-circuiting.</span></span>  <span data-ttu-id="93cf8-110">Jeśli jedna operacja w łańcuchu operacji dostępu i indeks warunkowa składowa zwraca nic, zatrzymuje pozostałą część wykonania łańcucha.</span><span class="sxs-lookup"><span data-stu-id="93cf8-110">If one operation in a chain of conditional member access and index operations returns Nothing, the rest of the chain’s execution stops.</span></span>  <span data-ttu-id="93cf8-111">W poniższym przykładzie C(E) nie są oceniane, jeśli `A`, `B`, lub `C` ocenia na wartość Nothing.</span><span class="sxs-lookup"><span data-stu-id="93cf8-111">In the following example, C(E) isn't evaluated if `A`, `B`, or `C` evaluates to Nothing.</span></span>

```vb
A?.B?.C?(E);
```

<span data-ttu-id="93cf8-112">Innym zastosowaniem uzyskać dostęp do elementu członkowskiego warunkowe null jest wywoływać delegatów w sposób wątkowo ze znacznie mniejszej ilości kodu.</span><span class="sxs-lookup"><span data-stu-id="93cf8-112">Another use for null-conditional member access is to invoke delegates in a thread-safe way with much less code.</span></span>  <span data-ttu-id="93cf8-113">Stary sposób wymaga kodu podobnego do poniższego:</span><span class="sxs-lookup"><span data-stu-id="93cf8-113">The old way requires code like the following:</span></span>  

```vb  
Dim handler = AddressOf(Me.PropertyChanged)  
If handler IsNot Nothing  
    Call handler(…)  
```

<span data-ttu-id="93cf8-114">Nowy sposób jest znacznie prostszy:</span><span class="sxs-lookup"><span data-stu-id="93cf8-114">The new way is much simpler:</span></span>  

```vb
PropertyChanged?.Invoke(…)
```

<span data-ttu-id="93cf8-115">Nowy sposób jest bezpieczny wątkowo, ponieważ kompilator generuje kod, aby sprawdzić stan `PropertyChanged` tylko jeden raz, a następnie zapisuje wynik w zmiennej tymczasowej.</span><span class="sxs-lookup"><span data-stu-id="93cf8-115">The new way is thread-safe because the compiler generates code to evaluate `PropertyChanged` one time only, keeping the result in a temporary variable.</span></span> <span data-ttu-id="93cf8-116">Metodę `Invoke`trzeba wywołać jawnie, ponieważ nie istnieje składnia `PropertyChanged?(e)` do wywołania delegata przy użyciu operatora warunkowego „null”.</span><span class="sxs-lookup"><span data-stu-id="93cf8-116">You need to explicitly call the `Invoke` method because there is no null-conditional delegate invocation syntax `PropertyChanged?(e)`.</span></span>  

## <a name="see-also"></a><span data-ttu-id="93cf8-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93cf8-117">See also</span></span>

- [<span data-ttu-id="93cf8-118">Operatory (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="93cf8-118">Operators (Visual Basic)</span></span>](index.md)
- [<span data-ttu-id="93cf8-119">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93cf8-119">Visual Basic Programming Guide</span></span>](../../../visual-basic/programming-guide/index.md)
- [<span data-ttu-id="93cf8-120">Dokumentacja języka Visual Basic</span><span class="sxs-lookup"><span data-stu-id="93cf8-120">Visual Basic Language Reference</span></span>](../../../visual-basic/language-reference/index.md)  
