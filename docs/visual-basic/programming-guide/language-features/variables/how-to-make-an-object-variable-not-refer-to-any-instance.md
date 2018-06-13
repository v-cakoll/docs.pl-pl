---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: bf918b762261e1dd1fc4161a10203f3d0067e454
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649727"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="aa049-102">Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aa049-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="aa049-103">Usuń skojarzenie zmienna obiektu z dowolnego wystąpienia obiektu przez ustawienie jej na [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="aa049-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="aa049-104">Aby usunąć skojarzenie z dowolnego wystąpienia obiektu zmienna obiektu</span><span class="sxs-lookup"><span data-stu-id="aa049-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="aa049-105">Ustaw zmienną na `Nothing` w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="aa049-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="aa049-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="aa049-106">Robust Programming</span></span>  
 <span data-ttu-id="aa049-107">Jeśli kod spróbuje uzyskiwanie dostępu do członka zmiennej obiektu, który został ustawiony na `Nothing`, <xref:System.NullReferenceException> występuje.</span><span class="sxs-lookup"><span data-stu-id="aa049-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="aa049-108">Jeśli ustawiono zmienną obiektu `Nothing` często, czy jest możliwe, zmienna nie jest zainicjowany, jest dobrze jest umieścić uzyskuje dostęp do elementu członkowskiego w `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="aa049-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="aa049-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="aa049-109">.NET Framework Security</span></span>  
 <span data-ttu-id="aa049-110">Jeśli użyjesz zmiennej obiektu dla obiektów, które zawierają dane poufne lub można ustawić zmiennej `Nothing` po ma się nie aktywnie do czynienia z jedną z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="aa049-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="aa049-111">Zmniejsza ryzyko złośliwy kod, aby uzyskać dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="aa049-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa049-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa049-112">See Also</span></span>  
 <xref:System.NullReferenceException>  
 [<span data-ttu-id="aa049-113">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="aa049-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [<span data-ttu-id="aa049-114">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="aa049-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [<span data-ttu-id="aa049-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="aa049-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)  
 [<span data-ttu-id="aa049-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="aa049-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
 [<span data-ttu-id="aa049-117">Rozwiązywanie problemów z wyjątkami: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="aa049-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](http://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
