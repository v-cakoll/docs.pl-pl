---
title: 'Instrukcje: Utwórz procedurę (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- Visual Basic code, reusing
- procedure declarations
- procedures [Visual Basic], about procedures
ms.assetid: 4f779247-0b50-47e8-9e5c-ab5cf39ac0d2
ms.openlocfilehash: 2cf4c788ec421c1e74ef7198496a92149e049752
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216718"
---
# <a name="how-to-create-a-procedure-visual-basic"></a><span data-ttu-id="3b5e1-102">Porady: Utwórz procedurę (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b5e1-102">How to: Create a Procedure (Visual Basic)</span></span>

<span data-ttu-id="3b5e1-103">Należy`Sub` ująć procedurę między początkową instrukcją deklaracji (lub `Function`) i kończącą się instrukcją deklaracji`End Sub` ( `End Function`lub).</span><span class="sxs-lookup"><span data-stu-id="3b5e1-103">You enclose a procedure between a starting declaration statement (`Sub` or `Function`) and an ending declaration statement (`End Sub` or `End Function`).</span></span> <span data-ttu-id="3b5e1-104">Cały kod procedury należy do tych instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-104">All the procedure's code lies between these statements.</span></span>

 <span data-ttu-id="3b5e1-105">Procedura nie może zawierać innej procedury, dlatego jej instrukcje początkowe i końcowe muszą znajdować się poza inną procedurą.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-105">A procedure cannot contain another procedure, so its starting and ending statements must be outside any other procedure.</span></span>

 <span data-ttu-id="3b5e1-106">Jeśli masz kod, który wykonuje to samo zadanie w różnych miejscach, możesz napisać zadanie jeden raz jako procedurę, a następnie wywołać ją z różnych miejsc w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-106">If you have code that performs the same task in different places, you can write the task once as a procedure and then call it from different places in your code.</span></span>

### <a name="to-create-a-procedure-that-does-not-return-a-value"></a><span data-ttu-id="3b5e1-107">Aby utworzyć procedurę, która nie zwraca wartości</span><span class="sxs-lookup"><span data-stu-id="3b5e1-107">To create a procedure that does not return a value</span></span>

1. <span data-ttu-id="3b5e1-108">Poza inną procedurą Użyj `Sub` instrukcji, a po niej `End Sub` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-108">Outside any other procedure, use a `Sub` statement, followed by an `End Sub` statement.</span></span>

2. <span data-ttu-id="3b5e1-109">W instrukcji należy `Sub` przestrzegać słowa kluczowego o nazwie procedury, a następnie listy parametrów w nawiasach. `Sub`</span><span class="sxs-lookup"><span data-stu-id="3b5e1-109">In the `Sub` statement, follow the `Sub` keyword with the name of the procedure, then the parameter list in parentheses.</span></span>

3. <span data-ttu-id="3b5e1-110">Umieść instrukcje kodu procedury między `Sub` instrukcjami i. `End Sub`</span><span class="sxs-lookup"><span data-stu-id="3b5e1-110">Place the procedure's code statements between the `Sub` and `End Sub` statements.</span></span>

### <a name="to-create-a-procedure-that-returns-a-value"></a><span data-ttu-id="3b5e1-111">Aby utworzyć procedurę zwracającą wartość</span><span class="sxs-lookup"><span data-stu-id="3b5e1-111">To create a procedure that returns a value</span></span>

1. <span data-ttu-id="3b5e1-112">Poza inną procedurą Użyj `Function` instrukcji, a po niej `End Function` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-112">Outside any other procedure, use a `Function` statement, followed by an `End Function` statement.</span></span>

2. <span data-ttu-id="3b5e1-113">W instrukcji wykonaj słowo kluczowe z nazwą procedury, następnie listę parametrów w nawiasach, a następnie `As` klauzulę określającą typ danych zwracanej wartości. `Function` `Function`</span><span class="sxs-lookup"><span data-stu-id="3b5e1-113">In the `Function` statement, follow the `Function` keyword with the name of the procedure, then the parameter list in parentheses, and then an `As` clause specifying the data type of the return value.</span></span>

3. <span data-ttu-id="3b5e1-114">Umieść instrukcje kodu procedury między `Function` instrukcjami i. `End Function`</span><span class="sxs-lookup"><span data-stu-id="3b5e1-114">Place the procedure's code statements between the `Function` and `End Function` statements.</span></span>

4. <span data-ttu-id="3b5e1-115">`Return` Użyj instrukcji, aby zwrócić wartość do kodu wywołującego.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-115">Use a `Return` statement to return the value to the calling code.</span></span>

### <a name="to-connect-your-new-procedure-with-the-old-repetitive-blocks-of-code"></a><span data-ttu-id="3b5e1-116">Aby połączyć swoją nową procedurę z starymi powtarzalnymi blokami kodu</span><span class="sxs-lookup"><span data-stu-id="3b5e1-116">To connect your new procedure with the old, repetitive blocks of code</span></span>

1. <span data-ttu-id="3b5e1-117">Upewnij się, że definiujesz nową procedurę w miejscu, do którego stary kod ma do niego dostęp.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-117">Make sure you define the new procedure in a place where the old code has access to it.</span></span>

2. <span data-ttu-id="3b5e1-118">W starym, powtarzającym się bloku kodu Zastąp instrukcje, które wykonują powtarzające się zadanie z pojedynczą `Sub` instrukcją, która wywołuje procedurę lub. `Function`</span><span class="sxs-lookup"><span data-stu-id="3b5e1-118">In your old, repetitive code block, replace the statements that perform the repetitive task with a single statement that calls the `Sub` or `Function` procedure.</span></span>

3. <span data-ttu-id="3b5e1-119">Jeśli procedura jest `Function` zwracająca wartość, upewnij się, że instrukcja wywołująca wykonuje akcję z zwracaną wartością, taką jak przechowywanie jej w zmiennej, lub w przeciwnym razie wartość zostanie utracona.</span><span class="sxs-lookup"><span data-stu-id="3b5e1-119">If your procedure is a `Function` that returns a value, ensure that your calling statement performs an action with the returned value, such as storing it in a variable, or else the value will be lost.</span></span>

## <a name="example"></a><span data-ttu-id="3b5e1-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b5e1-120">Example</span></span>

 <span data-ttu-id="3b5e1-121">Poniższa `Function` procedura oblicza najdłuższy Trójkąt lub przeciwprostokątnej, z prawej strony, z uwzględnieniem wartości pozostałych dwóch stron:</span><span class="sxs-lookup"><span data-stu-id="3b5e1-121">The following `Function` procedure calculates the longest side, or hypotenuse, of a right triangle, given the values for the other two sides:</span></span>

 [!code-vb[VbVbcnProcedures#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#1)]

## <a name="see-also"></a><span data-ttu-id="3b5e1-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3b5e1-122">See also</span></span>

- [<span data-ttu-id="3b5e1-123">Procedury</span><span class="sxs-lookup"><span data-stu-id="3b5e1-123">Procedures</span></span>](index.md)
- [<span data-ttu-id="3b5e1-124">Sub, procedury</span><span class="sxs-lookup"><span data-stu-id="3b5e1-124">Sub Procedures</span></span>](sub-procedures.md)
- [<span data-ttu-id="3b5e1-125">Procedury funkcji</span><span class="sxs-lookup"><span data-stu-id="3b5e1-125">Function Procedures</span></span>](function-procedures.md)
- [<span data-ttu-id="3b5e1-126">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="3b5e1-126">Property Procedures</span></span>](property-procedures.md)
- [<span data-ttu-id="3b5e1-127">Procedury operatorów</span><span class="sxs-lookup"><span data-stu-id="3b5e1-127">Operator Procedures</span></span>](operator-procedures.md)
- [<span data-ttu-id="3b5e1-128">Parametry i argumenty procedur</span><span class="sxs-lookup"><span data-stu-id="3b5e1-128">Procedure Parameters and Arguments</span></span>](procedure-parameters-and-arguments.md)
- [<span data-ttu-id="3b5e1-129">Procedury rekursywne</span><span class="sxs-lookup"><span data-stu-id="3b5e1-129">Recursive Procedures</span></span>](recursive-procedures.md)
- [<span data-ttu-id="3b5e1-130">Przeciążanie procedury</span><span class="sxs-lookup"><span data-stu-id="3b5e1-130">Procedure Overloading</span></span>](procedure-overloading.md)
- [<span data-ttu-id="3b5e1-131">Obiekty i klasy</span><span class="sxs-lookup"><span data-stu-id="3b5e1-131">Objects and Classes</span></span>](../objects-and-classes/index.md)
- [<span data-ttu-id="3b5e1-132">Programowanie zorientowane obiektowo (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b5e1-132">Object-Oriented Programming (Visual Basic)</span></span>](../../concepts/object-oriented-programming.md)
