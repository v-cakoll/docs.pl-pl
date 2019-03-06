---
title: Zmienne obiektów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: cc5be13293a89e73d1790e94a99d7936f1711e12
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57352974"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="acfd7-102">Zmienne obiektów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="acfd7-102">Object Variables in Visual Basic</span></span>

<span data-ttu-id="acfd7-103">Oprócz przechowywania wartości bezpośrednio, zmienna może odwoływać się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="acfd7-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="acfd7-104">Obiekt można przypisać do zmiennej powodów przypisane żadnej wartości dla zmiennej:</span><span class="sxs-lookup"><span data-stu-id="acfd7-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>

- <span data-ttu-id="acfd7-105">Nazwa zmiennej jest często krótsze i łatwiejsze do zapamiętania niż pełną ścieżkę metody i właściwości, które są niezbędne do dostępu do samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="acfd7-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>

- <span data-ttu-id="acfd7-106">Użycie zmiennej, która odwołuje się do obiektu jest bardziej wydajne niż wielokrotnie uzyskiwania dostępu do samego obiektu za pomocą niezbędne metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="acfd7-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>

- <span data-ttu-id="acfd7-107">Możesz zmienić zmienną do odwoływania się do innych obiektów, podczas gdy kod jest uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="acfd7-107">You can change a variable to refer to other objects while your code is running.</span></span>

## <a name="making-code-shorter"></a><span data-ttu-id="acfd7-108">Tworzenie kodu krótsze</span><span class="sxs-lookup"><span data-stu-id="acfd7-108">Making Code Shorter</span></span>

<span data-ttu-id="acfd7-109">Skrócenie czasu kod, który trzeba wpisać, można używać zmiennych obiektu.</span><span class="sxs-lookup"><span data-stu-id="acfd7-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="acfd7-110">W poniższym przykładzie użyto pełną ścieżkę, metod i właściwości w celu uzyskania dostępu do <xref:System.Windows.Forms.Control> obiektu.</span><span class="sxs-lookup"><span data-stu-id="acfd7-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>

```vb
' Assume Me is a valid Form, or replace Me with a valid Form.
Me.ActiveForm.ActiveControl.Text = "Test"
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)
Me.ActiveForm.ActiveControl.Show()
```

<span data-ttu-id="acfd7-111">Możesz skrócić ten kod i przyspieszyć wykonywanie, jeśli użyjesz zmiennej obiektu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="acfd7-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="acfd7-112">Należy zadeklarować zmienną obiektu z określonej klasy, który chcesz przypisać do niej (`Control` w tym przypadku).</span><span class="sxs-lookup"><span data-stu-id="acfd7-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="acfd7-113">Po przypisaniu obiektu do zmiennej, można traktować je dokładnie tak samo jak traktować obiektu, do którego odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="acfd7-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="acfd7-114">Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z metod.</span><span class="sxs-lookup"><span data-stu-id="acfd7-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="acfd7-115">W poniższym przykładzie użyto zmiennej obiektu w celu uproszczenia kodu w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="acfd7-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>

```vb
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl
ctrlActv.Text = "Test"
ctrlActv.Location = New Point(100, 100)
ctrlActv.Show()
```

## <a name="see-also"></a><span data-ttu-id="acfd7-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acfd7-116">See also</span></span>

- [<span data-ttu-id="acfd7-117">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="acfd7-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="acfd7-118">Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji</span><span class="sxs-lookup"><span data-stu-id="acfd7-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)
- [<span data-ttu-id="acfd7-119">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="acfd7-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)
- [<span data-ttu-id="acfd7-120">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="acfd7-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="acfd7-121">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="acfd7-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
