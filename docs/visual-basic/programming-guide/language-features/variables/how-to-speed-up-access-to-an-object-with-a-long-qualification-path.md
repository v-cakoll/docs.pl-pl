---
title: 'Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: 83670ae6af0904156b08398024658cf504b7663f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346817"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a><span data-ttu-id="c94da-102">Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c94da-102">How to: Speed Up Access to an Object with a Long Qualification Path (Visual Basic)</span></span>

<span data-ttu-id="c94da-103">Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżki kwalifikacji kilku metod i właściwości, możesz przyspieszyć kod, nie powtarzając się ścieżki kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="c94da-103">If you frequently access an object that requires a qualification path of several methods and properties, you can speed up your code by not repeating the qualification path.</span></span>

<span data-ttu-id="c94da-104">Istnieją dwa sposoby, aby uniknąć powtarzania ścieżki kwalifikacji.</span><span class="sxs-lookup"><span data-stu-id="c94da-104">There are two ways you can avoid repeating the qualification path.</span></span> <span data-ttu-id="c94da-105">Obiekt można przypisać do zmiennej lub użyć go w bloku `With`...`End With`.</span><span class="sxs-lookup"><span data-stu-id="c94da-105">You can assign the object to a variable, or you can use it in a `With`...`End With` block.</span></span>

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a><span data-ttu-id="c94da-106">Aby przyspieszyć dostęp do wysoce kwalifikowanego obiektu przez przypisanie go do zmiennej</span><span class="sxs-lookup"><span data-stu-id="c94da-106">To speed up access to a heavily qualified object by assigning it to a variable</span></span>

1. <span data-ttu-id="c94da-107">Zadeklaruj zmienną typu obiektu, do którego jest często uzyskiwany dostęp.</span><span class="sxs-lookup"><span data-stu-id="c94da-107">Declare a variable of the type of the object that you are accessing frequently.</span></span> <span data-ttu-id="c94da-108">Określ ścieżkę kwalifikacji w części inicjującej deklaracji.</span><span class="sxs-lookup"><span data-stu-id="c94da-108">Specify the qualification path in the initialization part of the declaration.</span></span>

    ```vb
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="c94da-109">Użyj zmiennej, aby uzyskać dostęp do elementów członkowskich obiektu.</span><span class="sxs-lookup"><span data-stu-id="c94da-109">Use the variable to access the object's members.</span></span>

    ```vb
    ctrlActv.Text = "Test"
    ctrlActv.Location = New Point(100, 100)
    ctrlActv.Show()
    ```

### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a><span data-ttu-id="c94da-110">Aby przyspieszyć dostęp do wysoce kwalifikowanego obiektu za pomocą... Koniec z blokiem</span><span class="sxs-lookup"><span data-stu-id="c94da-110">To speed up access to a heavily qualified object by using a With...End With block</span></span>

1. <span data-ttu-id="c94da-111">Umieść ścieżkę kwalifikacji w instrukcji `With`.</span><span class="sxs-lookup"><span data-stu-id="c94da-111">Put the qualification path in a `With` statement.</span></span>

    ```vb
    With someForm.ActiveForm.ActiveControl
    ```

2. <span data-ttu-id="c94da-112">Uzyskaj dostęp do elementów członkowskich obiektu wewnątrz bloku `With` przed instrukcją `End With`.</span><span class="sxs-lookup"><span data-stu-id="c94da-112">Access the object's members inside the `With` block, before the `End With` statement.</span></span>

    ```vb
        .Text = "Test"
        .Location = New Point(100, 100)
        .Show()
    End With
    ```

## <a name="see-also"></a><span data-ttu-id="c94da-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c94da-113">See also</span></span>

- [<span data-ttu-id="c94da-114">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="c94da-114">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="c94da-115">With...End With, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c94da-115">With...End With Statement</span></span>](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
