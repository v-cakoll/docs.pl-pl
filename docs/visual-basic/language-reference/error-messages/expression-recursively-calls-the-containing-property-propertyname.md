---
title: Wyrażenie cyklicznie wywołuje zawierającą je właściwość &#39; &lt;propertyname&gt;&#39;
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: f14e2645772b22a8f6ff2385dcd316a42d1d5cf0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="expression-recursively-calls-the-containing-property-39ltpropertynamegt39"></a><span data-ttu-id="d63ed-102">Wyrażenie cyklicznie wywołuje zawierającą je właściwość &#39; &lt;propertyname&gt;&#39;</span><span class="sxs-lookup"><span data-stu-id="d63ed-102">Expression recursively calls the containing property &#39;&lt;propertyname&gt;&#39;</span></span>
<span data-ttu-id="d63ed-103">Instrukcja w `Set` procedury definicji właściwości przechowuje wartość w nazwie właściwości.</span><span class="sxs-lookup"><span data-stu-id="d63ed-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="d63ed-104">Zalecane podejście do przechowywania wartości właściwości jest określenie `Private` zmiennej w kontenerze właściwości i używać go zarówno `Get` i `Set` procedur.</span><span class="sxs-lookup"><span data-stu-id="d63ed-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="d63ed-105">`Set` Procedury należy następnie przechowywać wartość przychodzącego w tym `Private` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="d63ed-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="d63ed-106">`Get` Procedury zachowuje się jak `Function` procedury, można przypisać wartości do nazwy właściwości i zwrócić kontrolkę przez napotkania `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="d63ed-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="d63ed-107">Zalecane podejście jest jednak zawierać `Private` zmiennej jako wartości w [zwracać instrukcji](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d63ed-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="d63ed-108">`Set` Procedury zachowuje się jak `Sub` procedury, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="d63ed-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="d63ed-109">W związku z tym nazwa procedura lub właściwość nie ma specjalnego znaczenia w `Set` procedura i nie można zapisać wartości do niego.</span><span class="sxs-lookup"><span data-stu-id="d63ed-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="d63ed-110">Poniższy przykład przedstawia podejście, które mogą być przyczyną tego błędu, następuje zalecane podejście.</span><span class="sxs-lookup"><span data-stu-id="d63ed-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
```  
Public Class illustrateProperties  
' The code in the following property causes this error.  
    Public Property badProp() As Char  
        Get  
            Dim charValue As Char  
            ' Insert code to update charValue.  
            badProp = charValue  
        End Get  
        Set(ByVal Value As Char)  
            ' The following statement causes this error.  
            badProp = Value  
            ' The value stored in the local variable badProp  
            ' is not used by the Get procedure in this property.  
        End Set  
    End Property  
' The following code uses the recommended approach.  
    Private propValue As Char  
    Public Property goodProp() As Char  
        Get  
            ' Insert code to update propValue.  
            Return propValue  
        End Get  
        Set(ByVal Value As Char)  
            propValue = Value  
        End Set  
    End Property  
End Class  
```  
  
 <span data-ttu-id="d63ed-111">Domyślnie ten komunikat jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="d63ed-111">By default, this message is a warning.</span></span> <span data-ttu-id="d63ed-112">Aby uzyskać więcej informacji na temat ukrywanie ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="d63ed-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="d63ed-113">**Identyfikator błędu:** BC42026</span><span class="sxs-lookup"><span data-stu-id="d63ed-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="d63ed-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="d63ed-114">To correct this error</span></span>  
  
-   <span data-ttu-id="d63ed-115">Należy zmodyfikować definicję właściwości do użycia zalecane podejście, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d63ed-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d63ed-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d63ed-116">See Also</span></span>  
 [<span data-ttu-id="d63ed-117">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="d63ed-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)  
 [<span data-ttu-id="d63ed-118">Property, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d63ed-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
 [<span data-ttu-id="d63ed-119">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="d63ed-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
