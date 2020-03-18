---
title: Zabezpieczenia i sytuacja wyścigu
'description:': Describes pitfalls to avoid around security holes exploited by race conditions, including dispose methods, constructors, cached objects, and finalizers.
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
ms.openlocfilehash: 09d8d0d6e85af04fe0fb00f53df408126012081e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186777"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="05b94-102">Zabezpieczenia i sytuacja wyścigu</span><span class="sxs-lookup"><span data-stu-id="05b94-102">Security and Race Conditions</span></span>
<span data-ttu-id="05b94-103">Innym obszarem zainteresowania jest możliwość luk w zabezpieczeniach wykorzystywanych przez warunki rasowe.</span><span class="sxs-lookup"><span data-stu-id="05b94-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="05b94-104">Istnieje kilka sposobów, w których może się to zdarzyć.</span><span class="sxs-lookup"><span data-stu-id="05b94-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="05b94-105">Podtematy, które następują zarys niektórych głównych pułapek, które deweloper musi unikać.</span><span class="sxs-lookup"><span data-stu-id="05b94-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="05b94-106">Warunki wyścigu w metodzie utylizacji</span><span class="sxs-lookup"><span data-stu-id="05b94-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="05b94-107">Jeśli klasy **Dispose** metody (aby uzyskać więcej informacji, zobacz [Wyrzucanie elementów bezużytecznych)](../../../docs/standard/garbage-collection/index.md)nie jest zsynchronizowany, jest możliwe, że kod oczyszczania wewnątrz **Dispose** można uruchomić więcej niż jeden raz, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05b94-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
    if (myObj != null)
    {  
        Cleanup(myObj);  
        myObj = null;  
    }  
}  
```  
  
 <span data-ttu-id="05b94-108">Ponieważ ta **implementacja Dispose** nie jest `Cleanup` zsynchronizowana, możliwe jest wywołanie przez `_myObj` pierwszy jeden wątek, a następnie drugi wątek, zanim **ustawiono wartość null**.</span><span class="sxs-lookup"><span data-stu-id="05b94-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="05b94-109">Czy jest to problem zabezpieczeń zależy `Cleanup` od tego, co się dzieje po uruchomieniu kodu.</span><span class="sxs-lookup"><span data-stu-id="05b94-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="05b94-110">Głównym problemem z niezsynchronizowane **Implementacje dispose** polega na użyciu dojścia zasobów, takich jak pliki.</span><span class="sxs-lookup"><span data-stu-id="05b94-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="05b94-111">Niewłaściwa utylizacja może spowodować niewłaściwe uchylnie, co często prowadzi do luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="05b94-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="05b94-112">Warunki wyścigu w konstruktorów</span><span class="sxs-lookup"><span data-stu-id="05b94-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="05b94-113">W niektórych aplikacjach może być możliwe dla innych wątków, aby uzyskać dostęp do elementów członkowskich klasy, zanim ich konstruktory klasy zostały całkowicie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="05b94-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="05b94-114">Należy przejrzeć wszystkie konstruktory klasy, aby upewnić się, że nie ma żadnych problemów z zabezpieczeniami, jeśli tak się stanie, lub w razie potrzeby zsynchronizować wątki.</span><span class="sxs-lookup"><span data-stu-id="05b94-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="05b94-115">Warunki wyścigu z obiektami buforowanymi</span><span class="sxs-lookup"><span data-stu-id="05b94-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="05b94-116">Kod, który buforuje informacje o zabezpieczeniach lub używa zabezpieczeń dostępu do kodu [Assert](../../../docs/framework/misc/using-the-assert-method.md) operacji może być również narażony na warunki wyścigu, jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05b94-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
```vb  
Sub SomeSecureFunction()  
    If SomeDemandPasses() Then  
        fCallersOk = True  
        DoOtherWork()  
        fCallersOk = False  
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
    if (SomeDemandPasses())
    {  
        fCallersOk = true;  
        DoOtherWork();  
        fCallersOk = false;  
    }  
}  
void DoOtherWork()
{  
    if (fCallersOK)
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
  
 <span data-ttu-id="05b94-117">Jeśli istnieją inne `DoOtherWork` ścieżki do tego można wywołać z innego wątku z tego samego obiektu, niezaufany obiekt wywołujący może poślizgu przeszłości popytu.</span><span class="sxs-lookup"><span data-stu-id="05b94-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="05b94-118">Jeśli kod buforuje informacje zabezpieczające, upewnij się, że sprawdzasz je pod kątem tej luki.</span><span class="sxs-lookup"><span data-stu-id="05b94-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="05b94-119">Warunki wyścigu w finalizatorów</span><span class="sxs-lookup"><span data-stu-id="05b94-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="05b94-120">Warunki wyścigu mogą również wystąpić w obiekcie, który odwołuje się do zasobu statycznego lub niezarządzanego, który następnie zwalnia w finalizatora.</span><span class="sxs-lookup"><span data-stu-id="05b94-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="05b94-121">Jeśli wiele obiektów współużytkuje zasób, który jest manipulowany w finalizatora klasy, obiekty muszą synchronizować cały dostęp do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="05b94-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05b94-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05b94-122">See also</span></span>

- [<span data-ttu-id="05b94-123">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="05b94-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
