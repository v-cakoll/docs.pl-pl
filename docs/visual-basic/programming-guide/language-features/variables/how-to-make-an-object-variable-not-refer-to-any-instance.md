---
title: 'Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia'
ms.date: 07/20/2015
helpviewer_keywords:
- Nothing keyword [Visual Basic], variable assignment
- object variables [Visual Basic], null reference
ms.assetid: e6d30578-bdae-4142-a3ac-a10697bf696a
ms.openlocfilehash: cce2e59cb76652937868a731ad308872d1aba2f3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410454"
---
# <a name="how-to-make-an-object-variable-not-refer-to-any-instance-visual-basic"></a><span data-ttu-id="16e26-102">Porady: sprawianie, aby zmienna obiektu nie odwoływała się do żadnego wystąpienia (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="16e26-102">How to: Make an Object Variable Not Refer to Any Instance (Visual Basic)</span></span>
<span data-ttu-id="16e26-103">Można usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu, ustawiając dla niego wartość [Nothing](../../../language-reference/nothing.md).</span><span class="sxs-lookup"><span data-stu-id="16e26-103">You can disassociate an object variable from any object instance by setting it to [Nothing](../../../language-reference/nothing.md).</span></span>  
  
### <a name="to-disassociate-an-object-variable-from-any-object-instance"></a><span data-ttu-id="16e26-104">Aby usunąć skojarzenie zmiennej obiektu z dowolnego wystąpienia obiektu</span><span class="sxs-lookup"><span data-stu-id="16e26-104">To disassociate an object variable from any object instance</span></span>  
  
- <span data-ttu-id="16e26-105">Ustaw zmienną na `Nothing` w instrukcji przypisania.</span><span class="sxs-lookup"><span data-stu-id="16e26-105">Set the variable to `Nothing` in an assignment statement.</span></span>  
  
    ```vb  
    ' Assume account is a defined class  
    Dim currentAccount As account  
    currentAccount = Nothing  
    ```  
  
## <a name="robust-programming"></a><span data-ttu-id="16e26-106">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="16e26-106">Robust Programming</span></span>  
 <span data-ttu-id="16e26-107">Jeśli kod próbuje uzyskać dostęp do elementu członkowskiego zmiennej obiektu, która została ustawiona na `Nothing` , <xref:System.NullReferenceException> występuje.</span><span class="sxs-lookup"><span data-stu-id="16e26-107">If your code tries to access a member of an object variable that has been set to `Nothing`, a <xref:System.NullReferenceException> occurs.</span></span> <span data-ttu-id="16e26-108">Jeśli zmienna obiektu jest ustawiana na `Nothing` często lub jeśli jest możliwe, zmienna nie jest zainicjowana, dobrym pomysłem jest zawrzeć dostęp do składowych w `Try...Catch...Finally` bloku.</span><span class="sxs-lookup"><span data-stu-id="16e26-108">If you set an object variable to `Nothing` frequently, or if it is possible the variable is not initialized, it is a good idea to enclose member accesses in a `Try...Catch...Finally` block.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="16e26-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="16e26-109">.NET Framework Security</span></span>  
 <span data-ttu-id="16e26-110">Jeśli używasz zmiennej obiektu dla obiektów, które zawierają dane poufne lub poufne, możesz ustawić zmienną na, `Nothing` gdy nie będziesz aktywnie korzystać z jednego z tych obiektów.</span><span class="sxs-lookup"><span data-stu-id="16e26-110">If you use an object variable for objects that contain confidential or sensitive data, you can set the variable to `Nothing` when you are not actively dealing with one of those objects.</span></span> <span data-ttu-id="16e26-111">Zmniejsza to prawdopodobieństwo złośliwego kodu, który uzyskuje dostęp do danych.</span><span class="sxs-lookup"><span data-stu-id="16e26-111">This reduces the chance of malicious code gaining access to the data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16e26-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16e26-112">See also</span></span>

- <xref:System.NullReferenceException>
- [<span data-ttu-id="16e26-113">Zmienne obiektów</span><span class="sxs-lookup"><span data-stu-id="16e26-113">Object Variables</span></span>](object-variables.md)
- [<span data-ttu-id="16e26-114">Przypisanie zmiennej obiektu</span><span class="sxs-lookup"><span data-stu-id="16e26-114">Object Variable Assignment</span></span>](object-variable-assignment.md)
- [<span data-ttu-id="16e26-115">Nothing</span><span class="sxs-lookup"><span data-stu-id="16e26-115">Nothing</span></span>](../../../language-reference/nothing.md)
- [<span data-ttu-id="16e26-116">Try...Catch...Finally, instrukcja</span><span class="sxs-lookup"><span data-stu-id="16e26-116">Try...Catch...Finally Statement</span></span>](../../../language-reference/statements/try-catch-finally-statement.md)
