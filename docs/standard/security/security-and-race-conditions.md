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
ms.openlocfilehash: 57ceaedc7c38ae70a0db5a7fd584a765a7474aff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933812"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="60638-102">Zabezpieczenia i sytuacja wyścigu</span><span class="sxs-lookup"><span data-stu-id="60638-102">Security and Race Conditions</span></span>
<span data-ttu-id="60638-103">Kolejnym obszarem kwestią jest potencjalnych luk w zabezpieczeniach wykorzystana przez wyścigu.</span><span class="sxs-lookup"><span data-stu-id="60638-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="60638-104">Istnieje kilka sposobów, w których może się to zdarzyć.</span><span class="sxs-lookup"><span data-stu-id="60638-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="60638-105">Tematy podrzędne, które należy wykonać opisano niektóre z najważniejszych pułapek, których należy unikać dewelopera.</span><span class="sxs-lookup"><span data-stu-id="60638-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="60638-106">Warunki wyścigu w metodzie Dispose</span><span class="sxs-lookup"><span data-stu-id="60638-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="60638-107">Jeśli klasa **Dispose** — metoda (Aby uzyskać więcej informacji, zobacz [wyrzucania elementów bezużytecznych](../../../docs/standard/garbage-collection/index.md)) jest nie jest zsynchronizowana, istnieje możliwość, ten kod porządkujący wewnątrz **Dispose** mogą być uruchamiane więcej niż jedno, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60638-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../../../docs/standard/garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="60638-108">Ponieważ to **Dispose** wdrożenia nie jest zsynchronizowana, możliwe jest `Cleanup` ma zostać wywołana przez najpierw jeden wątek, a następnie drugi wątek przed `_myObj` ustawiono **null**.</span><span class="sxs-lookup"><span data-stu-id="60638-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="60638-109">Czy to jest kwestią zabezpieczeń zależy od tego, co się stanie, gdy `Cleanup` kod działa.</span><span class="sxs-lookup"><span data-stu-id="60638-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="60638-110">Podstawowym problemem w niezsynchronizowane **Dispose** implementacje polega na użyciu tego dojścia zasobów, takich jak pliki.</span><span class="sxs-lookup"><span data-stu-id="60638-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="60638-111">Niewłaściwy usuwania może spowodować nieprawidłowe dojście ma być używany, co często prowadzi do luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="60638-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="60638-112">Warunki wyścigu w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="60638-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="60638-113">W niektórych aplikacji może być możliwe dla innych wątków do dostępu do składowych klasy, przed ich Konstruktory klasy całkowicie zostały uruchomione.</span><span class="sxs-lookup"><span data-stu-id="60638-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="60638-114">Należy przejrzeć wszystkie Konstruktory klasy, aby upewnić się, że nie występują żadne problemy zabezpieczeń, jeśli to powinno to być spowodowane lub synchronizacji wątków, jeśli to konieczne.</span><span class="sxs-lookup"><span data-stu-id="60638-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="60638-115">Warunki wyścigu przy użyciu buforowanych obiektów</span><span class="sxs-lookup"><span data-stu-id="60638-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="60638-116">Kod, który buforuje informacje o zabezpieczeniach lub wykorzystuje zabezpieczenia dostępu kodu [Asercja](../../../docs/framework/misc/using-the-assert-method.md) operacji może również występować sytuacje wyścigu w przypadku innych części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="60638-116">Code that caches security information or uses the code access security [Assert](../../../docs/framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="60638-117">W przypadku innych ścieżek do `DoOtherWork` którą można wywołać z innego wątku za pomocą tego samego obiektu, niezaufanych obiekt wywołujący poślizg wcześniejsze żądanie.</span><span class="sxs-lookup"><span data-stu-id="60638-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="60638-118">Jeśli Twój kod buforuje informacje o zabezpieczeniach, upewnij się, przejrzyj luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="60638-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="60638-119">Warunki wyścigu w finalizatory</span><span class="sxs-lookup"><span data-stu-id="60638-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="60638-120">Warunki wyścigu może również wystąpić w obiekcie, który odwołuje się do statycznego lub niezarządzany zasób, który następnie zwalnia jego finalizator.</span><span class="sxs-lookup"><span data-stu-id="60638-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="60638-121">Jeśli wiele obiektów dzielą jakiś zasób, który jest przetwarzany w finalizatory klasy, obiekty należy zsynchronizować wszelki dostęp do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="60638-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="60638-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="60638-122">See also</span></span>

- [<span data-ttu-id="60638-123">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="60638-123">Secure Coding Guidelines</span></span>](../../../docs/standard/security/secure-coding-guidelines.md)
