---
title: Zmienne obiektów
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 7eb860bc732f923316b8ce1d7b94ecdb368bfec3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351785"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="866ef-102">Zmienne obiektów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="866ef-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="866ef-103">Oprócz bezpośredniego zapisywania wartości zmienna może odwoływać się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="866ef-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="866ef-104">Przypisujesz obiekt do zmiennej z tych samych powodów, do których przypisano dowolną wartość do zmiennej:</span><span class="sxs-lookup"><span data-stu-id="866ef-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="866ef-105">Nazwa zmiennej jest często krótsza i łatwiejsza do zapamiętania niż pełna ścieżka metod i właściwości, które są niezbędne do uzyskania dostępu do samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="866ef-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="866ef-106">Użycie zmiennej odwołującej się do obiektu jest bardziej wydajne niż wielokrotne uzyskiwanie dostępu do samego obiektu za pomocą niezbędnych metod lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="866ef-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="866ef-107">Można zmienić zmienną, aby odwoływać się do innych obiektów, gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="866ef-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="866ef-108">Szybsze wprowadzanie kodu</span><span class="sxs-lookup"><span data-stu-id="866ef-108">Making Code Shorter</span></span>

<span data-ttu-id="866ef-109">Możesz użyć zmiennych obiektów, aby skrócić kod, który musisz wpisać.</span><span class="sxs-lookup"><span data-stu-id="866ef-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="866ef-110">W poniższym przykładzie zastosowano pełną ścieżkę metod i właściwości, aby uzyskać dostęp do obiektu <xref:System.Windows.Forms.Control>.</span><span class="sxs-lookup"><span data-stu-id="866ef-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="866ef-111">Możesz skrócić ten kod i przyspieszyć wykonywanie, jeśli używasz zmiennej obiektu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="866ef-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="866ef-112">Należy zadeklarować zmienną obiektu z określoną klasą, która ma zostać przypisana do niej (`Control` w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="866ef-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="866ef-113">Po przypisaniu obiektu do zmiennej można go traktować dokładnie tak samo, jak w przypadku obiektu, do którego się odwołuje.</span><span class="sxs-lookup"><span data-stu-id="866ef-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="866ef-114">Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z jej metod.</span><span class="sxs-lookup"><span data-stu-id="866ef-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="866ef-115">Poniższy przykład używa zmiennej obiektu do uproszczenia kodu w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="866ef-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="866ef-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="866ef-116">See also</span></span>

- [<span data-ttu-id="866ef-117">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="866ef-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="866ef-118">Instrukcje: przyspieszanie dostępu do obiektu z długą ścieżką kwalifikacji</span><span class="sxs-lookup"><span data-stu-id="866ef-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="866ef-119">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="866ef-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="866ef-120">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="866ef-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="866ef-121">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="866ef-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
