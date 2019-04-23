---
title: Zabezpieczanie obsługi wyjątków
ms.date: 03/30/2017
dev_langs:
- cpp
helpviewer_keywords:
- code security, exception handling
- security [.NET Framework], exception handling
- secure coding, exception handling
- exception handling, security
ms.assetid: 1f3da743-9742-47ff-96e6-d0dd1e9e1c19
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bc8cd20a4183ffd002f1399b6b50c8956208a21b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173683"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="8a571-102">Zabezpieczanie obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="8a571-102">Securing Exception Handling</span></span>
<span data-ttu-id="8a571-103">W programie Visual C++ i Visual Basic, wyrażenie filtru do dalszego w górę stosu jest uruchamiany przed każdą **na koniec** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a571-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="8a571-104">**Catch** bloku skojarzony z filtrem, który jest uruchamiany po **na koniec** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="8a571-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="8a571-105">Aby uzyskać więcej informacji, zobacz [wyjątki Using User-Filtered](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="8a571-105">For more information, see [Using User-Filtered Exceptions](../../../docs/standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="8a571-106">Tej części są rozpatrywane ryzyko związane z tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="8a571-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="8a571-107">Rozważmy następujący przykład pseudokodzie, który ilustruje kolejność, w której instrukcji filtrów i **na koniec** instrukcje uruchamiania.</span><span class="sxs-lookup"><span data-stu-id="8a571-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="8a571-108">Ten kod wyświetla następujące czynności.</span><span class="sxs-lookup"><span data-stu-id="8a571-108">This code prints the following.</span></span>  
  
```  
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="8a571-109">Filtr, który jest uruchamiany przed **na koniec** instrukcji, dzięki czemu problemy z zabezpieczeniami mogą zostać wprowadzone przez wszystko, co sprawia, że stan zmiany, których wykonanie innego kodu, możesz wykorzystać.</span><span class="sxs-lookup"><span data-stu-id="8a571-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="8a571-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="8a571-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="8a571-111">Ta pseudokodzie umożliwia filtr wyższego rzędu stosu do uruchamiania dowolnego kodu.</span><span class="sxs-lookup"><span data-stu-id="8a571-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="8a571-112">Inne przykłady działań, które będą miały ten sam efekt są tymczasowe personifikacja innego tożsamości, ustawienie flagi wewnętrznej omija niektóre sprawdzanie zabezpieczeń lub zmiana kulturę skojarzonych z wątkiem.</span><span class="sxs-lookup"><span data-stu-id="8a571-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="8a571-113">Zalecanym rozwiązaniem jest wprowadzenie obsługi wyjątków do izolowania zmian w kodzie na stan wątku z bloków filtru obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="8a571-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="8a571-114">Jednak należy prawidłowo wprowadzane obsługi wyjątków lub ten problem nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="8a571-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="8a571-115">Poniższy przykład zmienia kultura interfejsu użytkownika, ale podobnie narażeni każdego rodzaju zmiany stanu wątku.</span><span class="sxs-lookup"><span data-stu-id="8a571-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="8a571-116">Słuszność poprawki w tym przypadku jest opakowanie, istniejące **spróbuj**/**na koniec** bloku **spróbuj**/**catch** blok.</span><span class="sxs-lookup"><span data-stu-id="8a571-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="8a571-117">Po prostu Przedstawiamy **catch throw** klauzuli się z istniejącymi **spróbuj**/**na koniec** bloku nie rozwiąże problemu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="8a571-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="8a571-118">To nie rozwiąże problemu, ponieważ **na koniec** instrukcji nie został wcześniej uruchomiony `FilterFunc` przejmie kontrolę.</span><span class="sxs-lookup"><span data-stu-id="8a571-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="8a571-119">Poniższy przykład naprawia problem przez zapewnienie, że **na koniec** klauzuli zostało wykonane przed oferty wyjątek bloki filtru wyjątków obiekty wywołujące.</span><span class="sxs-lookup"><span data-stu-id="8a571-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8a571-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a571-120">See also</span></span>

- [<span data-ttu-id="8a571-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="8a571-121">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
