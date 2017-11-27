---
title: "Zmienne obiektów w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a><span data-ttu-id="9ef09-102">Zmienne obiektów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9ef09-102">Object Variables in Visual Basic</span></span>
<span data-ttu-id="9ef09-103">Oprócz wartości są przechowywane bezpośrednio, zmienna może odwoływać się do obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ef09-103">In addition to storing values directly, a variable can refer to an object.</span></span> <span data-ttu-id="9ef09-104">Obiekt można przypisać do zmiennej przyczyn przypisać wartości do zmiennej:</span><span class="sxs-lookup"><span data-stu-id="9ef09-104">You assign an object to a variable for the same reasons you assign any value to a variable:</span></span>  
  
-   <span data-ttu-id="9ef09-105">Nazwa zmiennej jest często krótsze i łatwiejsze do zapamiętania niż Pełna ścieżka metod i właściwości niezbędne dostępu do tego samego obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ef09-105">A variable name is often shorter and easier to remember than the full path of methods and properties necessary to access the object itself.</span></span>  
  
-   <span data-ttu-id="9ef09-106">Używanie zmiennej, która odwołuje się do obiektu jest bardziej efektywne niż wielokrotnie podczas uzyskiwania dostępu do obiektu za pomocą niezbędne metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="9ef09-106">Using a variable that refers to an object is more efficient than repeatedly accessing the object itself through the necessary methods or properties.</span></span>  
  
-   <span data-ttu-id="9ef09-107">Możesz zmienić zmiennej, aby odwoływać się do innych obiektów, gdy wykonywany jest kod.</span><span class="sxs-lookup"><span data-stu-id="9ef09-107">You can change a variable to refer to other objects while your code is running.</span></span>  
  
## <a name="making-code-shorter"></a><span data-ttu-id="9ef09-108">Tworzenie krótszą kodu</span><span class="sxs-lookup"><span data-stu-id="9ef09-108">Making Code Shorter</span></span>  
 <span data-ttu-id="9ef09-109">Zmienne obiektów służy do skrócenia kod, który trzeba wpisywać.</span><span class="sxs-lookup"><span data-stu-id="9ef09-109">You can use object variables to shorten the code you have to type.</span></span> <span data-ttu-id="9ef09-110">W poniższym przykładzie użyto pełnej ścieżki właściwości i metod dostępu do <xref:System.Windows.Forms.Control> obiektu.</span><span class="sxs-lookup"><span data-stu-id="9ef09-110">The following example uses the full path of methods and properties to access a <xref:System.Windows.Forms.Control> object.</span></span>  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 <span data-ttu-id="9ef09-111">Możesz skrócić ten kod i przyspieszenia wykonywania, jeśli użyjesz zmiennej obiektu dla formantu.</span><span class="sxs-lookup"><span data-stu-id="9ef09-111">You can shorten this code, and speed up execution, if you use an object variable for the control.</span></span> <span data-ttu-id="9ef09-112">Należy zadeklarować zmienną obiektu o określonej klasy, który chcesz przypisać do niej (`Control` w takim przypadku).</span><span class="sxs-lookup"><span data-stu-id="9ef09-112">You should declare the object variable with the specific class that you intend to assign to it (`Control` in this case).</span></span> <span data-ttu-id="9ef09-113">Po przypisaniu obiektu do zmiennej można traktować go dokładnie tak samo jak traktować obiektu, do którego odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="9ef09-113">Once you assign an object to the variable, you can treat it exactly the same as you treat the object to which it refers.</span></span> <span data-ttu-id="9ef09-114">Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z metod.</span><span class="sxs-lookup"><span data-stu-id="9ef09-114">You can set or retrieve the properties of the object or use any of its methods.</span></span> <span data-ttu-id="9ef09-115">W poniższym przykładzie użyto zmiennej obiektu uprościć kod w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9ef09-115">The following example uses an object variable to simplify the code in the preceding example.</span></span>  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a><span data-ttu-id="9ef09-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9ef09-116">See Also</span></span>  
 [<span data-ttu-id="9ef09-117">Deklaracja zmiennej</span><span class="sxs-lookup"><span data-stu-id="9ef09-117">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="9ef09-118">Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji</span><span class="sxs-lookup"><span data-stu-id="9ef09-118">How to: Speed Up Access to an Object with a Long Qualification Path</span></span>](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [<span data-ttu-id="9ef09-119">Deklaracja zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="9ef09-119">Object Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [<span data-ttu-id="9ef09-120">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="9ef09-120">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="9ef09-121">Wartości zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="9ef09-121">Object Variable Values</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
