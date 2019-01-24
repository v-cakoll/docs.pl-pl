---
title: 'Instrukcje: Sprawianie Aby zmienna obiektu nie odwoływała się do dowolnego wystąpienia (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: 1199fa4e126c3d15e56a6c895aecf6afcae17f0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54678515"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="ae2ea-102">Instrukcje: Sprawianie Aby zmienna obiektu nie odwoływała się do dowolnego wystąpienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ae2ea-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="ae2ea-103">Usuń skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu przez ustawienie [nic](../../../../visual-basic/language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="ae2ea-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../../visual-basic/language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="ae2ea-104">Aby usunąć skojarzenie z dowolnego wystąpienia obiektu zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="ae2ea-104">To disassociate an object variable from any object instance</span></span>  
  
-   <span data-ttu-id="ae2ea-105">Ustaw zmienną na `Nothing` w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="ae2ea-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="ae2ea-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="ae2ea-106">Robust Programming</span></span>  
 <span data-ttu-id="ae2ea-107">Jeśli kod próbuje uzyskać dostępu do członka zmienną obiektu, który został ustawiony na `Nothing`, <xref:System.NullReferenceException> występuje.</span><span class="sxs-lookup"><span data-stu-id="ae2ea-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="ae2ea-108">Jeśli zmienna obiektu jest ustawiona na `Nothing` często, lub jeśli jest to możliwe, zmienna nie została zainicjowana, to dobry pomysł, aby ująć dostępie do elementów członkowskich w `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="ae2ea-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="ae2ea-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="ae2ea-109">.NET Framework Security</span></span>  
 <span data-ttu-id="ae2ea-110">Użycie zmiennej obiektu dla obiektów, które zawierają dane poufne, można ustawić zmiennej `Nothing` kiedy masz nie aktywnie do czynienia z jedną z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ae2ea-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="ae2ea-111">Zmniejsza to prawdopodobieństwo złośliwego kodu, uzyskiwanie dostępu do danych.</span><span class="sxs-lookup"><span data-stu-id="ae2ea-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ae2ea-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ae2ea-112">See also</span></span>
- <xref:System.NullReferenceException>
- [<span data-ttu-id="ae2ea-113">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="ae2ea-113">Object Variables</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [<span data-ttu-id="ae2ea-114">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="ae2ea-114">Object Variable Assignment</span></span>](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)
- [<span data-ttu-id="ae2ea-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="ae2ea-115">Nothing</span></span>](../../../../visual-basic/language-reference/nothing.md)
- [<span data-ttu-id="ae2ea-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="ae2ea-116">Try...Catch...Finally Statement</span></span>](../../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)
- [<span data-ttu-id="ae2ea-117">Rozwiązywanie problemów z wyjątkami: System.NullReferenceException</span><span class="sxs-lookup"><span data-stu-id="ae2ea-117">Troubleshooting Exceptions: System.NullReferenceException</span></span>](https://msdn.microsoft.com/library/4822b0b4-8105-43fb-887a-3cc51ff02899)
