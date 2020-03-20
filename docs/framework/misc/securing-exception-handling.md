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
ms.openlocfilehash: ad27e62197f6fdaa6b5e706f4ae02c03fecae9f1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181139"
---
# <a name="securing-exception-handling"></a><span data-ttu-id="01d0a-102">Zabezpieczanie obsługi wyjątków</span><span class="sxs-lookup"><span data-stu-id="01d0a-102">Securing Exception Handling</span></span>
<span data-ttu-id="01d0a-103">W językach Visual C++ i Visual Basic wyrażenie filtru dalej w górę stosu jest uruchamiane przed dowolną **instrukcją finally.**</span><span class="sxs-lookup"><span data-stu-id="01d0a-103">In Visual C++ and Visual Basic, a filter expression further up the stack runs before any **finally** statement.</span></span> <span data-ttu-id="01d0a-104">Blok **catch** skojarzony z tym filtrem jest uruchamiany po instrukcji **finally.**</span><span class="sxs-lookup"><span data-stu-id="01d0a-104">The **catch** block associated with that filter runs after the **finally** statement.</span></span> <span data-ttu-id="01d0a-105">Aby uzyskać więcej informacji, zobacz [Korzystanie z wyjątków filtrowanych przez użytkownika](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span><span class="sxs-lookup"><span data-stu-id="01d0a-105">For more information, see [Using User-Filtered Exceptions](../../standard/exceptions/using-user-filtered-exception-handlers.md).</span></span> <span data-ttu-id="01d0a-106">W tej sekcji przeanalizowano implikacje dla bezpieczeństwa tej kolejności.</span><span class="sxs-lookup"><span data-stu-id="01d0a-106">This section examines the security implications of this order.</span></span> <span data-ttu-id="01d0a-107">Należy wziąć pod uwagę następujący przykład pseudokodu, który ilustruje kolejność uruchamiania instrukcji filtrowania i instrukcji **finally.**</span><span class="sxs-lookup"><span data-stu-id="01d0a-107">Consider the following pseudocode example that illustrates the order in which filter statements and **finally** statements run.</span></span>  
  
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
  
 <span data-ttu-id="01d0a-108">Ten kod drukuje następujące.</span><span class="sxs-lookup"><span data-stu-id="01d0a-108">This code prints the following.</span></span>  
  
```output
Throw  
Filter  
Finally  
Catch  
```  
  
 <span data-ttu-id="01d0a-109">Filtr jest uruchamiany przed **instrukcją finally,** więc problemy z zabezpieczeniami mogą być wprowadzane przez wszystko, co powoduje zmianę stanu, w którym wykonanie innego kodu może skorzystać.</span><span class="sxs-lookup"><span data-stu-id="01d0a-109">The filter runs before the **finally** statement, so security issues can be introduced by anything that makes a state change where execution of other code could take advantage.</span></span> <span data-ttu-id="01d0a-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="01d0a-110">For example:</span></span>  
  
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
  
 <span data-ttu-id="01d0a-111">Ten pseudokod umożliwia filtr wyżej stosu, aby uruchomić dowolny kod.</span><span class="sxs-lookup"><span data-stu-id="01d0a-111">This pseudocode allows a filter higher up the stack to run arbitrary code.</span></span> <span data-ttu-id="01d0a-112">Inne przykłady operacji, które mogłyby mieć podobny efekt, to tymczasowe personifikacja innej tożsamości, ustawienie flagi wewnętrznej, która omija niektóre sprawdzanie zabezpieczeń lub zmiana kultury skojarzonej z wątkiem.</span><span class="sxs-lookup"><span data-stu-id="01d0a-112">Other examples of operations that would have a similar effect are temporary impersonation of another identity, setting an internal flag that bypasses some security check, or changing the culture associated with the thread.</span></span> <span data-ttu-id="01d0a-113">Zalecane rozwiązanie jest wprowadzenie obsługi wyjątków do izolowania zmian kodu do stanu wątku z bloków filtrów wywołujących.</span><span class="sxs-lookup"><span data-stu-id="01d0a-113">The recommended solution is to introduce an exception handler to isolate the code's changes to thread state from callers' filter blocks.</span></span> <span data-ttu-id="01d0a-114">Jednak ważne jest, aby program obsługi wyjątków został prawidłowo wprowadzony lub ten problem nie zostanie rozwiązany.</span><span class="sxs-lookup"><span data-stu-id="01d0a-114">However, it is important that the exception handler be properly introduced or this problem will not be fixed.</span></span> <span data-ttu-id="01d0a-115">W poniższym przykładzie przełącza kultury interfejsu użytkownika, ale wszelkiego rodzaju zmiany stanu wątku może być podobnie widoczne.</span><span class="sxs-lookup"><span data-stu-id="01d0a-115">The following example switches the UI culture, but any kind of thread state change could be similarly exposed.</span></span>  
  
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
  
 <span data-ttu-id="01d0a-116">Poprawną poprawką w tym przypadku jest zawijanie istniejącej **próby**/**ostatecznie** bloku w bloku catch **try.**/**catch**</span><span class="sxs-lookup"><span data-stu-id="01d0a-116">The correct fix in this case is to wrap the existing **try**/**finally** block in a **try**/**catch** block.</span></span> <span data-ttu-id="01d0a-117">Po prostu wprowadzenie **catch-throw** klauzuli do istniejącej **try**/**finally** bloku nie rozwiązuje problemu, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="01d0a-117">Simply introducing a **catch-throw** clause into the existing **try**/**finally** block does not fix the problem, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="01d0a-118">To nie rozwiązuje problemu, ponieważ **instrukcja finally** nie została uruchomiony przed `FilterFunc` pobiera kontroli.</span><span class="sxs-lookup"><span data-stu-id="01d0a-118">This does not fix the problem because the **finally** statement has not run before the `FilterFunc` gets control.</span></span>  
  
 <span data-ttu-id="01d0a-119">Poniższy przykład rozwiązuje problem, upewniając się, że **finally** klauzula została wykonana przed oferowaniem wyjątku się bloków filtru wyjątków wywołujących.</span><span class="sxs-lookup"><span data-stu-id="01d0a-119">The following example fixes the problem by ensuring that the **finally** clause has executed before offering an exception up the callers' exception filter blocks.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d0a-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01d0a-120">See also</span></span>

- [<span data-ttu-id="01d0a-121">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="01d0a-121">Secure Coding Guidelines</span></span>](../../standard/security/secure-coding-guidelines.md)
