---
title: "Zabezpieczanie obsługi wyjątków"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 548606a0196012fdd21bf5512e8ea7b089c723ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="securing-exception-handling"></a><span data-ttu-id="ad4bb-102">Zabezpieczanie obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="ad4bb-102">Securing Exception Handling</span></span>
<span data-ttu-id="ad4bb-103">W programie Visual C++ i Visual Basic, wyrażenie filtru dalsze górę stosu jest uruchamiany przed każdą **koniec** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="ad4bb-104">**Catch** blok skojarzonych z tym filtru jest uruchamiany po **finally** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="ad4bb-105">Aby uzyskać więcej informacji, zobacz [wyjątki Using User-Filtered](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="ad4bb-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="ad4bb-106">W tej sekcji sprawdza, czy zabezpieczenia tego zamówienia.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="ad4bb-107">Należy wziąć pod uwagę w poniższym przykładzie pseudocode, która ilustruje kolejności, w których instrukcji filtrów i **koniec** instrukcje uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
```cpp  
void Main()   
{  
    try   
    {  
        Sub();  
    }   
    except (Filter())   
    {  
        Console.WriteLine("catch");  
    }  
}  
bool Filter () {  
    Console.WriteLine("filter");  
    return true;  
}  
void Sub()   
{  
    try   
    {  
        Console.WriteLine("throw");  
        throw new Exception();  
    }   
    finally   
    {  
        Console.WriteLine("finally");  
    }  
}                        
```  
  
 <span data-ttu-id="ad4bb-108">Ten kod wyświetla następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="ad4bb-109">Filtr jest uruchamiany przed **koniec** instrukcji, więc problemy dotyczące zabezpieczeń mogą zostać wprowadzone przez wszystko, co sprawia, że stan zmienianie, gdzie wykonywanie innych kodu można wykorzystać.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="ad4bb-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="ad4bb-110">For example:</span></span>  
  
```cpp  
try   
{  
    Alter_Security_State();  
    // This means changing anything (state variables,  
    // switching unmanaged context, impersonation, and   
    // so on) that could be exploited if malicious   
    // code ran before state is restored.  
    Do_some_work();  
}   
finally   
{  
    Restore_Security_State();  
    // This simply restores the state change above.  
}  
```  
  
 <span data-ttu-id="ad4bb-111">Ta pseudocode umożliwia filtr górę stosu do uruchomienia dowolnego kodu.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="ad4bb-112">Inne przykłady działań, które będą miały ten sam efekt są tymczasowe podszywania się pod innego tożsamości, ustawienie flaga wewnętrzna omija niektóre sprawdzania zabezpieczeń lub zmiana kultura skojarzonym z wątkiem.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="ad4bb-113">Zalecanym rozwiązaniem jest wprowadzenie obsługi wyjątków do izolowania zmiany kodu do stanu wątku z bloków filtr wywołań.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="ad4bb-114">Jest ważne, czy program obsługi wyjątku prawidłowo wprowadzić lub, ten problem nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="ad4bb-115">Poniższy przykład zmienia kultury interfejsu użytkownika, ale podobnie narażeni każdego rodzaju zmiany stanu wątku.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
   CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
   try {  
      Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
      // Do something that throws an exception.  
}  
   finally {  
      Thread.CurrentThread.CurrentUICulture = saveCulture;  
   }  
}  
```  
  
```vb  
Public Class UserCode  
   Public Shared Sub Main()  
      Try  
         Dim obj As YourObject = new YourObject  
         obj.YourMethod()  
      Catch e As Exception When FilterFunc  
         Console.WriteLine("An error occurred: '{0}'", e)  
         Console.WriteLine("Current Culture: {0}",   
Thread.CurrentThread.CurrentUICulture)  
      End Try  
   End Sub  
  
   Public Function FilterFunc As Boolean  
      Console.WriteLine("Current Culture: {0}", Thread.CurrentThread.CurrentUICulture)  
      Return True  
   End Sub  
  
End Class  
```  
  
 <span data-ttu-id="ad4bb-116">Poprawne w tym przypadku będzie opakowywać istniejące **spróbuj**/**koniec** blok w **spróbuj**/**catch** blok.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="ad4bb-117">Po prostu wprowadzenie **catch throw** klauzuli do istniejącego **spróbuj**/**koniec** bloku nie rozwiąże to problemu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
  
    try   
    {  
        Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
        // Do something that throws an exception.  
    }  
    catch { throw; }  
    finally   
    {  
        Thread.CurrentThread.CurrentUICulture = saveCulture;  
    }  
}  
```  
  
 <span data-ttu-id="ad4bb-118">To nie rozwiąże problemu, ponieważ **koniec** instrukcji nie został wcześniej uruchomiony `FilterFunc` pobiera formant.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="ad4bb-119">Poniższy przykład problem został rozwiązany przez zapewnienie, że **koniec** klauzuli zostało wykonane przed oferty wyjątek się bloki filtru wyjątków wywołań.</span><span class="sxs-lookup"><span data-stu-id="ad4bb-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
```cpp  
YourObject.YourMethod()  
{  
    CultureInfo saveCulture = Thread.CurrentThread.CurrentUICulture;  
    try    
    {  
        try   
        {  
            Thread.CurrentThread.CurrentUICulture = new CultureInfo("de-DE");  
            // Do something that throws an exception.  
        }  
        finally   
        {  
            Thread.CurrentThread.CurrentUICulture = saveCulture;  
        }  
    }  
    catch { throw; }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ad4bb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ad4bb-120">See Also</span></span>  
 [<span data-ttu-id="ad4bb-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="ad4bb-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
