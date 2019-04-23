---
title: 'Instrukcje: Tworzenie procedury (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 56099d334a03e85b816cf48983cbbead0784ef5b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59320395"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="272ce-102">Instrukcje: Tworzenie procedury (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="272ce-102">How to: Create a Procedure (Visual Basic)</span></span>
<span data-ttu-id="272ce-103">Ujmij procedury między początkową instrukcji deklaracji (`Sub` lub `Function`) i końcowej instrukcji deklaracji (`End Sub` lub `End Function`).</span><span class="sxs-lookup"><span data-stu-id="272ce-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="272ce-104">Kod wszystkie procedury musi się mieścić tych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272ce-104">All the procedure's code lies between these statements.</span></span>  
  
 <span data-ttu-id="272ce-105">Procedury nie może zawierać innej procedury, dzięki czemu jej instrukcji początkowy i końcowy musi znajdować się poza inne procedury.</span><span class="sxs-lookup"><span data-stu-id="272ce-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>  
  
 <span data-ttu-id="272ce-106">Jeśli masz kod, który wykonuje tego samego zadania w różnych miejscach, możesz zapisać zadanie raz jako procedura i wywołać go z różnych miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="272ce-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>  
  
### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="272ce-107">Aby utworzyć procedurę, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="272ce-107">To create a procedure that does not return a value</span></span>  
  
1. <span data-ttu-id="272ce-108">Poza innej procedury, należy użyć `Sub` instrukcji, następuje `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272ce-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>  
  
2. <span data-ttu-id="272ce-109">W `Sub` instrukcji, postępuj zgodnie z `Sub` — słowo kluczowe o nazwie procedury, a następnie lista parametrów w nawiasach.</span><span class="sxs-lookup"><span data-stu-id="272ce-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>  
  
3. <span data-ttu-id="272ce-110">Umieść instrukcje kod procedury między `Sub` i `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272ce-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>  
  
### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="272ce-111">Aby utworzyć procedurę, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="272ce-111">To create a procedure that returns a value</span></span>  
  
1. <span data-ttu-id="272ce-112">Poza innej procedury, należy użyć `Function` instrukcji, następuje `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272ce-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>  
  
2. <span data-ttu-id="272ce-113">W `Function` instrukcji, postępuj zgodnie z `Function` — słowo kluczowe o nazwie procedury, a następnie lista parametrów w nawiasach, a następnie `As` klauzuli określający typ danych wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="272ce-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>  
  
3. <span data-ttu-id="272ce-114">Umieść instrukcje kod procedury między `Function` i `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="272ce-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>  
  
4. <span data-ttu-id="272ce-115">Użyj `Return` instrukcji, aby zwrócić wartości do wywołującego kodu.</span><span class="sxs-lookup"><span data-stu-id="272ce-115">Use a `Return` statement to return the value to the calling code.</span></span>  
  
### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="272ce-116">Nawiązywanie połączeń z nową procedurę z stare, powtarzających się bloki kodu</span><span class="sxs-lookup"><span data-stu-id="272ce-116">To connect your new procedure with the old, repetitive blocks of code</span></span>  
  
1. <span data-ttu-id="272ce-117">Upewnij się, że należy zdefiniować nową procedurę w miejscu, w której stary kod ma do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="272ce-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>  
  
2. <span data-ttu-id="272ce-118">W bloku kodu stary i powtarzalnych, Zastąp instrukcji, które wykonują powtarzających się zadań przy użyciu pojedynczej instrukcji, która wywołuje `Sub` lub `Function` procedury.</span><span class="sxs-lookup"><span data-stu-id="272ce-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>  
  
3. <span data-ttu-id="272ce-119">Jeśli procedura jest `Function` zwracającego wartość, upewnij się, że instrukcji wywołujący wykonuje akcję z wartością zwróconą, takich jak przechowywanie ich w zmiennej, w przeciwnym razie wartość zostaną utracone.</span><span class="sxs-lookup"><span data-stu-id="272ce-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>  
  
## <a name="example"></a><span data-ttu-id="272ce-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="272ce-120">Example</span></span>  
 <span data-ttu-id="272ce-121">Następujące `Function` procedury oblicza najdłuższy bok lub przeciwprostokątnej trójkąta prostokątnego, biorąc pod uwagę wartości dla obu stron.</span><span class="sxs-lookup"><span data-stu-id="272ce-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides.</span></span>  
  
 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="272ce-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="272ce-122">See also</span></span>

- [<span data-ttu-id="272ce-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="272ce-123">Procedures</span></span>](./index.md)
- [<span data-ttu-id="272ce-124">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="272ce-124">Sub Procedures</span></span>](./sub-procedures.md)
- [<span data-ttu-id="272ce-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="272ce-125">Function Procedures</span></span>](./function-procedures.md)
- [<span data-ttu-id="272ce-126">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="272ce-126">Property Procedures</span></span>](./property-procedures.md)
- [<span data-ttu-id="272ce-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="272ce-127">Operator Procedures</span></span>](./operator-procedures.md)
- [<span data-ttu-id="272ce-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="272ce-128">Procedure Parameters and Arguments</span></span>](./procedure-parameters-and-arguments.md)
- [<span data-ttu-id="272ce-129">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="272ce-129">Recursive Procedures</span></span>](./recursive-procedures.md)
- [<span data-ttu-id="272ce-130">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="272ce-130">Procedure Overloading</span></span>](./procedure-overloading.md)
- [<span data-ttu-id="272ce-131">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="272ce-131">Objects and Classes</span></span>](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
- [<span data-ttu-id="272ce-132">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="272ce-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
