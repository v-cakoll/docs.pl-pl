---
title: "Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="0a1c2-102">Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0a1c2-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>
<span data-ttu-id="0a1c2-103">Jeśli często dostępu do obiektu, który wymaga ścieżką kwantyfikacji kilka metod i właściwości można przyspieszyć kodu nie powtarzając ścieżką kwantyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>  
  
 <span data-ttu-id="0a1c2-104">Istnieją dwa sposoby można uniknąć powtarzania ścieżką kwantyfikacji.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="0a1c2-105">Obiekt można przypisać do zmiennej lub używania go w `With`... `End With` bloku.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="0a1c2-106">Aby przyspieszyć dostępu do obiektu silnie kwalifikowana przez przypisanie go do zmiennej</span><span class="sxs-lookup"><span data-stu-id="0a1c2-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>  
  
1.  <span data-ttu-id="0a1c2-107">Deklarowanie zmiennej typu obiektu, którego uzyskujesz dostęp do często.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="0a1c2-108">Określ ścieżkę kwalifikacji w części inicjowania deklaracji.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-108">Specify the qualification path in the initialization part of the declaration.</span></span>  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="0a1c2-109">Dostęp do elementów członkowskich obiektu za pomocą zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-109">Use the variable to access the object's members.</span></span>  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="0a1c2-110">Aby przyspieszyć dostępu do obiektu silnie kwalifikowanej przy użyciu With... Blok końcowy z</span><span class="sxs-lookup"><span data-stu-id="0a1c2-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>  
  
1.  <span data-ttu-id="0a1c2-111">Umieść ścieżką kwantyfikacji w `With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-111">Put the qualification path in a `With` statement.</span></span>  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  <span data-ttu-id="0a1c2-112">Dostęp do elementów członkowskich obiektu wewnątrz `With` zablokować przed `End With` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="0a1c2-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="0a1c2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a1c2-113">See Also</span></span>  
 [<span data-ttu-id="0a1c2-114">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="0a1c2-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="0a1c2-115">Z... End With — instrukcja</span><span class="sxs-lookup"><span data-stu-id="0a1c2-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
