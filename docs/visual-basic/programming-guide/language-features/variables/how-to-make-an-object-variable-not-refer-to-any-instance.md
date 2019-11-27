---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 320dadb61c12f3339c5328dcef31c41503892c56
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74352895"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="6b884-102">Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6b884-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="6b884-103">Można usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu, ustawiając dla niego wartość [Nothing](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="6b884-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="6b884-104">Aby usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="6b884-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="6b884-105">Ustaw zmienną na `Nothing` w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="6b884-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="6b884-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="6b884-106">Robust Programming</span></span>  
 <span data-ttu-id="6b884-107">Jeśli kod próbuje uzyskać dostęp do elementu członkowskiego zmiennej obiektu, która została ustawiona na `Nothing`, wystąpi <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="6b884-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="6b884-108">Jeśli ustawisz zmienną obiektu na `Nothing` często lub jeśli jest możliwe, że zmienna nie została zainicjowana, dobrym pomysłem będzie zawrzeć dostęp do elementów członkowskich w bloku `Try...Catch...Finally`.</span><span class="sxs-lookup"><span data-stu-id="6b884-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="6b884-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="6b884-109">.NET Framework Security</span></span>  
 <span data-ttu-id="6b884-110">Jeśli używasz zmiennej obiektu dla obiektów, które zawierają dane poufne lub poufne, możesz ustawić zmienną do `Nothing`, gdy nie będziesz aktywnie korzystać z jednego z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="6b884-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="6b884-111">Zmniejsza to prawdopodobieństwo złośliwego kodu, który uzyskuje dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="6b884-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6b884-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6b884-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="6b884-113">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="6b884-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="6b884-114">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="6b884-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="6b884-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="6b884-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="6b884-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="6b884-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
