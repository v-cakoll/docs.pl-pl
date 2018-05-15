---
title: Zabezpieczenia i sytuacja wyścigu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [.NET Framework], race conditions
- race conditions
- secure coding, race conditions
- code security, race conditions
ms.assetid: ea3edb80-b2e8-4e85-bfed-311b20cb59b6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fdfc4d9e9ba3653bd1a762767e3c39a4f62e587a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="09219-102">Zabezpieczenia i sytuacja wyścigu</span><span class="sxs-lookup"><span data-stu-id="09219-102">Security and Race Conditions</span></span>
<span data-ttu-id="09219-103">Inny obszar dotyczą jest potencjalnych luk w zabezpieczeniach wykorzystana przez wyścigu.</span><span class="sxs-lookup"><span data-stu-id="09219-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="09219-104">Istnieje kilka sposobów, w których taka sytuacja może wystąpić.</span><span class="sxs-lookup"><span data-stu-id="09219-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="09219-105">Tematy podrzędne, które należy wykonać opisano niektóre z najważniejszych problemów, które należy unikać dewelopera.</span><span class="sxs-lookup"><span data-stu-id="09219-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="09219-106">Warunki wyścigu w metodzie Dispose</span><span class="sxs-lookup"><span data-stu-id="09219-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="09219-107">Jeśli klasa **Dispose** — metoda (Aby uzyskać więcej informacji, zobacz [wyrzucanie elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md)) jest nie są zsynchronizowane, możliwe jest oczyszczanie kodu wewnątrz **Dispose** może działać więcej niż jedno, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09219-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
```vb  
Sub Dispose()  
    If Not (myObj Is Nothing) Then  
       Cleanup(myObj)  
       myObj = Nothing  
    End If  
End Sub  
```  
  
```csharp  
void Dispose()   
{  
    if( myObj != null )   
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="09219-108">Ponieważ to **Dispose** implementacja nie są zsynchronizowane, istnieje możliwość `Cleanup` ma zostać wywołana przez wątek pierwszy z nich, a następnie drugi wątek przed `_myObj` ustawiono **null**.</span><span class="sxs-lookup"><span data-stu-id="09219-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="09219-109">Czy jest to problem dotyczący zabezpieczeń zależy od tego, co się stanie, gdy `Cleanup` kod działa.</span><span class="sxs-lookup"><span data-stu-id="09219-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="09219-110">Główne problem z niezsynchronizowane **Dispose** implementacje polega na użyciu dojść zasobów, takich jak pliki.</span><span class="sxs-lookup"><span data-stu-id="09219-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="09219-111">Niewłaściwy usuwania może spowodować nieprawidłowe dojście mają być używane, która często prowadzi do luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="09219-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="09219-112">Warunki wyścigu w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="09219-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="09219-113">W niektórych aplikacjach może być możliwe na inne wątki na dostęp do elementów członkowskich klasy, przed ich konstruktorów klas całkowicie zostało uruchomione.</span><span class="sxs-lookup"><span data-stu-id="09219-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="09219-114">Należy przejrzeć wszystkie konstruktorów klas, aby upewnić się, że nie ma żadnych zabezpieczeń problemów, jeśli to powinien być lub synchronizowanie wątków w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="09219-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="09219-115">Warunki wyścigu buforowanych obiektów</span><span class="sxs-lookup"><span data-stu-id="09219-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="09219-116">Kod, który przechowuje informacje o zabezpieczeniach lub używa zabezpieczenia dostępu kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operacji może również być narażony na ataki wyścigu Jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="09219-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False()  
    End If  
End Sub  
  
Sub DoOtherWork()  
    If fCallersOK Then  
        DoSomethingTrusted()  
    Else  
        DemandSomething()  
        DoSomethingTrusted()  
    End If  
End Sub  
```  
  
```csharp  
void SomeSecureFunction()   
{  
    if(SomeDemandPasses())   
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false();  
    }  
}  
void DoOtherWork()   
{  
    if( fCallersOK )   
    {  
        DoSomethingTrusted();  
    }  
    else   
    {  
        DemandSomething();  
        DoSomethingTrusted();  
    }  
}  
```  
  
 <span data-ttu-id="09219-117">Jeśli istnieją inne ścieżki do `DoOtherWork` który można wywołać z wątku innego za pomocą tego samego obiektu, niezaufanej wywołujący może dostawy popyt w przeszłości.</span><span class="sxs-lookup"><span data-stu-id="09219-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="09219-118">Jeśli kod buforuje informacje o zabezpieczeniach, upewnij się, przejrzyj luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="09219-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="09219-119">Warunki wyścigu w finalizatory</span><span class="sxs-lookup"><span data-stu-id="09219-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="09219-120">Warunki wyścigu może również wystąpić w obiekt, który odwołuje się do zasobu statyczne lub niezarządzane, który następnie powoduje zwolnienie w jego finalizator.</span><span class="sxs-lookup"><span data-stu-id="09219-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="09219-121">Jeśli wiele obiektów korzystają z zasobem, który jest przetwarzane w finalizator klasy, obiekty musi zsynchronizować dostęp do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="09219-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09219-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="09219-122">See Also</span></span>  
 [<span data-ttu-id="09219-123">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="09219-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
