---
title: Wyrażenie cyklicznie wywołuje zawierającą właściwość „<propertyname>”
ms.date: 07/20/2015
f1_keywords:
- vbc42026
- BC42026
helpviewer_keywords:
- BC42026
ms.assetid: 4fde9db6-3bf3-48dc-8e05-981bf08969da
ms.openlocfilehash: 9382c6b6850036f3ca3795f0aa80f49b892c0a5e
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259764"
---
# <a name="expression-recursively-calls-the-containing-property-propertyname"></a><span data-ttu-id="2f07e-102">Wyrażenie cyklicznie wywołuje zawierającą właściwość "\<propertyname >"</span><span class="sxs-lookup"><span data-stu-id="2f07e-102">Expression recursively calls the containing property '\<propertyname>'</span></span>
<span data-ttu-id="2f07e-103">Instrukcja w `Set` procedury definicji właściwości przechowuje wartość do nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="2f07e-103">A statement in the `Set` procedure of a property definition stores a value into the name of the property.</span></span>  
  
 <span data-ttu-id="2f07e-104">Zalecane podejście do przechowywania wartości właściwości jest zdefiniowanie `Private` zmiennej w kontenerze właściwości i używać go w obu `Get` i `Set` procedur.</span><span class="sxs-lookup"><span data-stu-id="2f07e-104">The recommended approach to holding the value of a property is to define a `Private` variable in the property's container and use it in both the `Get` and `Set` procedures.</span></span> <span data-ttu-id="2f07e-105">`Set` Procedury należy następnie przechowywać wartość przychodzącego w tym `Private` zmiennej.</span><span class="sxs-lookup"><span data-stu-id="2f07e-105">The `Set` procedure should then store the incoming value in this `Private` variable.</span></span>  
  
 <span data-ttu-id="2f07e-106">`Get` Procedury zachowuje się jak `Function` procedury, dzięki czemu można przypisać wartości do danej nazwy właściwości i przywrócenie kontroli przez napotkania `End Get` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2f07e-106">The `Get` procedure behaves like a `Function` procedure, so it can assign a value to the property name and return control by encountering the `End Get` statement.</span></span> <span data-ttu-id="2f07e-107">Zalecanym podejściem jest jednak obejmują `Private` zmiennej jako wartości w [instrukcji Return](../../../visual-basic/language-reference/statements/return-statement.md).</span><span class="sxs-lookup"><span data-stu-id="2f07e-107">The recommended approach, however, is to include the `Private` variable as the value in a [Return Statement](../../../visual-basic/language-reference/statements/return-statement.md).</span></span>  
  
 <span data-ttu-id="2f07e-108">`Set` Procedury zachowuje się jak `Sub` procedury, która nie zwraca wartości.</span><span class="sxs-lookup"><span data-stu-id="2f07e-108">The `Set` procedure behaves like a `Sub` procedure, which does not return a value.</span></span> <span data-ttu-id="2f07e-109">W związku z tym, nazwa procedura lub właściwość nie ma specjalnego znaczenia w ramach `Set` procedury, a nie można zapisać wartości do niego.</span><span class="sxs-lookup"><span data-stu-id="2f07e-109">Therefore, the procedure or property name has no special meaning within a `Set` procedure, and you cannot store a value into it.</span></span>  
  
 <span data-ttu-id="2f07e-110">Poniższy przykład przedstawia podejście, które może być przyczyną tego błędu, a następnie zalecane podejście.</span><span class="sxs-lookup"><span data-stu-id="2f07e-110">The following example illustrates the approach that can cause this error, followed by the recommended approach.</span></span>  
  
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
  
 <span data-ttu-id="2f07e-111">Domyślnie ta wiadomość jest ostrzeżenie.</span><span class="sxs-lookup"><span data-stu-id="2f07e-111">By default, this message is a warning.</span></span> <span data-ttu-id="2f07e-112">Aby uzyskać więcej informacji na temat ukrywania ostrzeżenia lub traktowanie ostrzeżeń jako błędy, zobacz [Konfigurowanie ostrzeżeń w języku Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span><span class="sxs-lookup"><span data-stu-id="2f07e-112">For more information about hiding warnings or treating warnings as errors, please see [Configuring Warnings in Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).</span></span>  
  
 <span data-ttu-id="2f07e-113">**Identyfikator błędu:** BC42026</span><span class="sxs-lookup"><span data-stu-id="2f07e-113">**Error ID:** BC42026</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="2f07e-114">Aby poprawić ten błąd</span><span class="sxs-lookup"><span data-stu-id="2f07e-114">To correct this error</span></span>  
  
-   <span data-ttu-id="2f07e-115">Należy zmodyfikować definicję właściwości do użycia zalecane podejście, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="2f07e-115">Rewrite the property definition to use the recommended approach as illustrated in the preceding example.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f07e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2f07e-116">See also</span></span>
- [<span data-ttu-id="2f07e-117">Procedury właściwości</span><span class="sxs-lookup"><span data-stu-id="2f07e-117">Property Procedures</span></span>](../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md)
- [<span data-ttu-id="2f07e-118">Instrukcja Property</span><span class="sxs-lookup"><span data-stu-id="2f07e-118">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)
- [<span data-ttu-id="2f07e-119">Set, instrukcja</span><span class="sxs-lookup"><span data-stu-id="2f07e-119">Set Statement</span></span>](../../../visual-basic/language-reference/statements/set-statement.md)
