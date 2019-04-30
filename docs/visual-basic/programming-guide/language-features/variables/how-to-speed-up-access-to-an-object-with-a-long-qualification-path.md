---
title: 'Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769047"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="e0eaf-102">Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e0eaf-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="e0eaf-103">Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżką kwalifikacji kilka metod i właściwości, można przyspieszyć swój kod, powtarzając nie ścieżką kwantyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="e0eaf-104">Istnieją dwa sposoby, można uniknąć powtarzania ścieżką kwantyfikacji.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="e0eaf-105">Obiekt można przypisać do zmiennej lub może używać go w `With`... `End With` bloku.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="e0eaf-106">Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie, przypisując go do zmiennej</span><span class="sxs-lookup"><span data-stu-id="e0eaf-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1. <span data-ttu-id="e0eaf-107">Zadeklaruj zmienną typu obiektu, którego uzyskujesz dostęp do często.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="e0eaf-108">Określ ścieżkę kwalifikacji w inicjowania część deklaracji.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="e0eaf-109">Dostęp do elementów członkowskich obiektu za pomocą zmiennej.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="e0eaf-110">Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie korzystając z... Blok końcowy z</span><span class="sxs-lookup"><span data-stu-id="e0eaf-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1. <span data-ttu-id="e0eaf-111">Umieść ścieżką kwantyfikacji w `With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. <span data-ttu-id="e0eaf-112">Dostęp do członków obiektu wewnątrz `With` block przed `End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e0eaf-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="e0eaf-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e0eaf-113">See also</span></span>

- [<span data-ttu-id="e0eaf-114">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="e0eaf-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="e0eaf-115">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e0eaf-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
