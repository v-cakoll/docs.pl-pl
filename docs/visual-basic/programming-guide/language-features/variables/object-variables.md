---
title: Zmienne obiektów w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
ms.openlocfilehash: 8383261c1806732c4c8abea9834000f003a848a0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649116"
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="414d3-102">Zmienne obiektów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="414d3-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="414d3-103">Oprócz wartości są przechowywane bezpośrednio, zmienna może odwoływać się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="414d3-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="414d3-104">Obiekt można przypisać do zmiennej przyczyn przypisać wartości do zmiennej:</span><span class="sxs-lookup"><span data-stu-id="414d3-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="414d3-105">Nazwa zmiennej jest często krótsze i łatwiejsze do zapamiętania niż Pełna ścieżka metod i właściwości niezbędne dostępu do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="414d3-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="414d3-106">Używanie zmiennej, która odwołuje się do obiektu jest bardziej efektywne niż wielokrotnie podczas uzyskiwania dostępu do obiektu za pomocą niezbędne metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="414d3-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="414d3-107">Możesz zmienić zmiennej, aby odwoływać się do innych obiektów, gdy wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="414d3-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="414d3-108">Tworzenie krótszą kodu</span><span class="sxs-lookup"><span data-stu-id="414d3-108">Making Code Shorter</span></span>  
 <span data-ttu-id="414d3-109">Zmienne obiektów służy do skrócenia kod, który trzeba wpisywać.</span><span class="sxs-lookup"><span data-stu-id="414d3-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="414d3-110">W poniższym przykładzie użyto pełnej ścieżki właściwości i metod dostępu do <xref:System.Windows.Forms.Control> obiektu.</span><span class="sxs-lookup"><span data-stu-id="414d3-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="414d3-111">Możesz skrócić ten kod i przyspieszenia wykonywania, jeśli użyjesz zmiennej obiektu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="414d3-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="414d3-112">Należy zadeklarować zmienną obiektu o określonej klasy, który chcesz przypisać do niej (`Control` w takim przypadku).</span><span class="sxs-lookup"><span data-stu-id="414d3-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="414d3-113">Po przypisaniu obiektu do zmiennej można traktować go dokładnie tak samo jak traktować obiektu, do którego odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="414d3-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="414d3-114">Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z metod.</span><span class="sxs-lookup"><span data-stu-id="414d3-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="414d3-115">W poniższym przykładzie użyto zmiennej obiektu uprościć kod w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="414d3-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="414d3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="414d3-116">See Also</span></span>  
 [<span data-ttu-id="414d3-117">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="414d3-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="414d3-118">Instrukcje: przyspieszanie dostępu do obiektu z długą ścieżką kwalifikacji</span><span class="sxs-lookup"><span data-stu-id="414d3-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="414d3-119">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="414d3-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="414d3-120">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="414d3-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="414d3-121">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="414d3-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
