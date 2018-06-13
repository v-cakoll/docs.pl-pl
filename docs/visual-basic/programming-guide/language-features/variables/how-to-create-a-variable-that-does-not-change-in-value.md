---
title: 'Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: d63c254abe6d12c094e0d1252c9721f668947f09
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33651379"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="5d4de-102">Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5d4de-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>
<span data-ttu-id="5d4de-103">Pojęcia zmienna, która nie zmienia jej wartość może się wydawać sprzeczne.</span><span class="sxs-lookup"><span data-stu-id="5d4de-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="5d4de-104">Istnieją sytuacje, gdy stałej nie jest możliwe, ale warto mieć zmiennej z wartością stałą.</span><span class="sxs-lookup"><span data-stu-id="5d4de-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="5d4de-105">W takim przypadku można zdefiniować zmienną członkowską z [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5d4de-105">In such a case you can define a member variable with the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
 <span data-ttu-id="5d4de-106">Nie można użyć [instrukcja Const](../../../../visual-basic/language-reference/statements/const-statement.md) Aby zadeklarować i przypisać wartość stałą w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="5d4de-106">You cannot use the [Const Statement](../../../../visual-basic/language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>  
  
-   <span data-ttu-id="5d4de-107">`Const` Instrukcji nie akceptuje typu danych, którego chcesz użyć</span><span class="sxs-lookup"><span data-stu-id="5d4de-107">The `Const` statement does not accept the data type you want to use</span></span>  
  
-   <span data-ttu-id="5d4de-108">Nie wiadomo, wartość w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="5d4de-108">You do not know the value at compile time</span></span>  
  
-   <span data-ttu-id="5d4de-109">Nie można obliczyć wartości stałej w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="5d4de-109">You are unable to compute the constant value at compile time</span></span>  
  
### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="5d4de-110">Aby utworzyć zmienną, która nie zmienia wartości</span><span class="sxs-lookup"><span data-stu-id="5d4de-110">To create a variable that does not change in value</span></span>  
  
1.  <span data-ttu-id="5d4de-111">Na poziomie modułu, należy zadeklarować zmienną członkowską z [instrukcji Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)i obejmują [tylko do odczytu](../../../../visual-basic/language-reference/modifiers/readonly.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="5d4de-111">At module level, declare a member variable with the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md) keyword.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted  
    ```  
  
     <span data-ttu-id="5d4de-112">Można określić `ReadOnly` tylko w zmiennej członkowskiej.</span><span class="sxs-lookup"><span data-stu-id="5d4de-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="5d4de-113">Oznacza to, że należy zdefiniować zmiennej na poziomie modułu, poza dowolnej procedury.</span><span class="sxs-lookup"><span data-stu-id="5d4de-113">This means you must define the variable at module level, outside of any procedure.</span></span>  
  
2.  <span data-ttu-id="5d4de-114">Jeśli można obliczyć wartości w jednej instrukcji w czasie kompilacji, użyj klauzuli inicjowania w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="5d4de-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="5d4de-115">Postępuj zgodnie z [jako](../../../../visual-basic/language-reference/statements/as-clause.md) klauzuli znakiem równości (`=`), a następnie za pomocą wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="5d4de-115">Follow the [As](../../../../visual-basic/language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="5d4de-116">Upewnij się, że kompilator może służyć do oceny tego wyrażenia stałej wartości.</span><span class="sxs-lookup"><span data-stu-id="5d4de-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>  
  
    ```  
    Dim ReadOnly timeStarted As Date = Now  
    ```  
  
     <span data-ttu-id="5d4de-117">Można przypisać wartości do `ReadOnly` zmiennej tylko raz.</span><span class="sxs-lookup"><span data-stu-id="5d4de-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="5d4de-118">Po wykonaniu żaden kod kiedykolwiek można zmienić jej wartość.</span><span class="sxs-lookup"><span data-stu-id="5d4de-118">Once you do so, no code can ever change its value.</span></span>  
  
     <span data-ttu-id="5d4de-119">Jeśli nie znasz wartość w czasie kompilacji lub nie można obliczyć w czasie kompilacji w jednej instrukcji, można go przypisać w czasie wykonywania w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="5d4de-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="5d4de-120">Aby to zrobić, należy zadeklarować `ReadOnly` zmiennej na poziomie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="5d4de-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="5d4de-121">W Konstruktorze tej klasy lub struktury obliczania wartości ustalonej zmiennej i przypisz go do zmiennej przed powrotem z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="5d4de-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d4de-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5d4de-122">See Also</span></span>  
 [<span data-ttu-id="5d4de-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="5d4de-123">WriteOnly</span></span>](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [<span data-ttu-id="5d4de-124">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="5d4de-124">Const Statement</span></span>](../../../../visual-basic/language-reference/statements/const-statement.md)
