---
title: 'Porady: tworzenie zmiennej, która nie zmienia wartości'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], read-only
- variables [Visual Basic], constant value
ms.assetid: 86b59266-25df-4635-ae15-9b59c411d036
ms.openlocfilehash: 04e08784b5cfbdeb6db73b9b00fe9afa201bd06d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410519"
---
# <a name="how-to-create-a-variable-that-does-not-change-in-value-visual-basic"></a><span data-ttu-id="34697-102">Porady: tworzenie zmiennej, która nie zmienia wartości (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="34697-102">How to: Create a Variable that Does Not Change in Value (Visual Basic)</span></span>

<span data-ttu-id="34697-103">Pojęcie zmiennej, która nie zmienia jej wartości, może wydawać się sprzeczne.</span><span class="sxs-lookup"><span data-stu-id="34697-103">The notion of a variable that does not change its value might appear to be contradictory.</span></span> <span data-ttu-id="34697-104">Istnieją jednak sytuacje, w których stała nie jest wykonalna i warto mieć zmienną o stałej wartości.</span><span class="sxs-lookup"><span data-stu-id="34697-104">But there are situations when a constant is not feasible and it is useful to have a variable with a fixed value.</span></span> <span data-ttu-id="34697-105">W takim przypadku można zdefiniować zmienną elementu członkowskiego za pomocą słowa kluczowego [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="34697-105">In such a case you can define a member variable with the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

<span data-ttu-id="34697-106">Nie można użyć [instrukcji const](../../../language-reference/statements/const-statement.md) do zadeklarowania i przypisania wartości stałej w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="34697-106">You cannot use the [Const Statement](../../../language-reference/statements/const-statement.md) to declare and assign a constant value in the following circumstances:</span></span>

- <span data-ttu-id="34697-107">`Const`Instrukcja nie akceptuje typu danych, którego chcesz użyć</span><span class="sxs-lookup"><span data-stu-id="34697-107">The `Const` statement does not accept the data type you want to use</span></span>

- <span data-ttu-id="34697-108">Nie znasz wartości w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="34697-108">You do not know the value at compile time</span></span>

- <span data-ttu-id="34697-109">Nie można obliczyć wartości stałej w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="34697-109">You are unable to compute the constant value at compile time</span></span>

### <a name="to-create-a-variable-that-does-not-change-in-value"></a><span data-ttu-id="34697-110">Aby utworzyć zmienną, która nie zmienia wartości</span><span class="sxs-lookup"><span data-stu-id="34697-110">To create a variable that does not change in value</span></span>

1. <span data-ttu-id="34697-111">Na poziomie modułu należy zadeklarować zmienną członkowską przy użyciu [instrukcji Dim](../../../language-reference/statements/dim-statement.md)i dołączyć słowo kluczowe [ReadOnly](../../../language-reference/modifiers/readonly.md) .</span><span class="sxs-lookup"><span data-stu-id="34697-111">At module level, declare a member variable with the [Dim Statement](../../../language-reference/statements/dim-statement.md), and include the [ReadOnly](../../../language-reference/modifiers/readonly.md) keyword.</span></span>

    ```vb
    Dim ReadOnly timeStarted
    ```

    <span data-ttu-id="34697-112">Można określić `ReadOnly` tylko dla zmiennej składowej.</span><span class="sxs-lookup"><span data-stu-id="34697-112">You can specify `ReadOnly` only on a member variable.</span></span> <span data-ttu-id="34697-113">Oznacza to, że należy zdefiniować zmienną na poziomie modułu poza procedurą.</span><span class="sxs-lookup"><span data-stu-id="34697-113">This means you must define the variable at module level, outside of any procedure.</span></span>

2. <span data-ttu-id="34697-114">Jeśli można obliczyć wartość w pojedynczej instrukcji w czasie kompilacji, należy użyć klauzuli inicjacji w `Dim` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="34697-114">If you can compute the value in a single statement at compile time, use an initialization clause in the `Dim` statement.</span></span> <span data-ttu-id="34697-115">Postępuj zgodnie z klauzulą [as](../../../language-reference/statements/as-clause.md) znaku równości ( `=` ), po którym następuje wyrażenie.</span><span class="sxs-lookup"><span data-stu-id="34697-115">Follow the [As](../../../language-reference/statements/as-clause.md) clause with an equal sign (`=`), followed by an expression.</span></span> <span data-ttu-id="34697-116">Upewnij się, że kompilator może oszacować to wyrażenie jako wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="34697-116">Be sure the compiler can evaluate this expression to a constant value.</span></span>

    ```vb
    Dim ReadOnly timeStarted As Date = Now
    ```

    <span data-ttu-id="34697-117">Można przypisać wartość do `ReadOnly` zmiennej tylko raz.</span><span class="sxs-lookup"><span data-stu-id="34697-117">You can assign a value to a `ReadOnly` variable only once.</span></span> <span data-ttu-id="34697-118">Gdy to zrobisz, żaden kod nie może zmienić jego wartości.</span><span class="sxs-lookup"><span data-stu-id="34697-118">Once you do so, no code can ever change its value.</span></span>

    <span data-ttu-id="34697-119">Jeśli nie znasz wartości w czasie kompilacji lub nie można obliczyć jej w czasie kompilacji w jednej instrukcji, można nadal przypisać ją w czasie wykonywania w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="34697-119">If you do not know the value at compile time, or cannot compute it at compile time in a single statement, you can still assign it at run time in a constructor.</span></span> <span data-ttu-id="34697-120">Aby to zrobić, należy zadeklarować `ReadOnly` zmienną na poziomie klasy lub struktury.</span><span class="sxs-lookup"><span data-stu-id="34697-120">To do this, you must declare the `ReadOnly` variable at class or structure level.</span></span> <span data-ttu-id="34697-121">W konstruktorze dla tej klasy lub struktury Oblicz ustaloną wartość zmiennej i przypisz ją do zmiennej przed zwróceniem z konstruktora.</span><span class="sxs-lookup"><span data-stu-id="34697-121">In the constructor for that class or structure, compute the variable's fixed value, and assign it to the variable before returning from the constructor.</span></span>

## <a name="see-also"></a><span data-ttu-id="34697-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34697-122">See also</span></span>

- [<span data-ttu-id="34697-123">WriteOnly</span><span class="sxs-lookup"><span data-stu-id="34697-123">WriteOnly</span></span>](../../../language-reference/modifiers/writeonly.md)
- [<span data-ttu-id="34697-124">Const, instrukcja</span><span class="sxs-lookup"><span data-stu-id="34697-124">Const Statement</span></span>](../../../language-reference/statements/const-statement.md)
