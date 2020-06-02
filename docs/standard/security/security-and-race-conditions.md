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
ms.openlocfilehash: 715bf240a5f7f44ba3f914ad6788631074aa41b2
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84291022"
---
# <a name="security-and-race-conditions"></a><span data-ttu-id="26df5-102">Zabezpieczenia i sytuacja wyścigu</span><span class="sxs-lookup"><span data-stu-id="26df5-102">Security and Race Conditions</span></span>
<span data-ttu-id="26df5-103">Innym obszarem zainteresowania jest potencjalna liczba luk w zabezpieczeniach wykorzystywanych przez sytuacje wyścigu.</span><span class="sxs-lookup"><span data-stu-id="26df5-103">Another area of concern is the potential for security holes exploited by race conditions.</span></span> <span data-ttu-id="26df5-104">Może się to zdarzyć na kilka sposobów.</span><span class="sxs-lookup"><span data-stu-id="26df5-104">There are several ways in which this might happen.</span></span> <span data-ttu-id="26df5-105">Tematy podrzędne, które przestrzegają konspektu, niektórych głównych pułapek, które muszą być unikane przez dewelopera.</span><span class="sxs-lookup"><span data-stu-id="26df5-105">The subtopics that follow outline some of the major pitfalls that the developer must avoid.</span></span>  
  
## <a name="race-conditions-in-the-dispose-method"></a><span data-ttu-id="26df5-106">Warunki wyścigu w metodzie Dispose</span><span class="sxs-lookup"><span data-stu-id="26df5-106">Race Conditions in the Dispose Method</span></span>  
 <span data-ttu-id="26df5-107">Jeśli metoda **Dispose** klasy (Aby uzyskać więcej informacji, zobacz [zbieranie elementów bezużytecznych](../garbage-collection/index.md)) nie jest zsynchronizowana, istnieje możliwość, że kod czyszczący wewnątrz elementu **Dispose** można uruchomić więcej niż jeden raz, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="26df5-107">If a class's **Dispose** method (for more information, see [Garbage Collection](../garbage-collection/index.md)) is not synchronized, it is possible that cleanup code inside **Dispose** can be run more than once, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="26df5-108">Ponieważ ta implementacja **usuwania** nie jest zsynchronizowana, można ją `Cleanup` wywołać przez pierwszy wątek, a następnie drugi wątek przed `_myObj` ustawieniem **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="26df5-108">Because this **Dispose** implementation is not synchronized, it is possible for `Cleanup` to be called by first one thread and then a second thread before `_myObj` is set to **null**.</span></span> <span data-ttu-id="26df5-109">To, czy jest to problem dotyczący zabezpieczeń, zależy od tego, co się dzieje, gdy `Cleanup` kod zostanie uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="26df5-109">Whether this is a security concern depends on what happens when the `Cleanup` code runs.</span></span> <span data-ttu-id="26df5-110">Istotny problem z niezsynchronizowanymi implementacjami **Dispose** obejmuje użycie dojścia do zasobów, takich jak pliki.</span><span class="sxs-lookup"><span data-stu-id="26df5-110">A major issue with unsynchronized **Dispose** implementations involves the use of resource handles such as files.</span></span> <span data-ttu-id="26df5-111">Niewłaściwe usunięcie może spowodować niewłaściwe użycie, które często prowadzi do luk w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="26df5-111">Improper disposal can cause the wrong handle to be used, which often leads to security vulnerabilities.</span></span>  
  
## <a name="race-conditions-in-constructors"></a><span data-ttu-id="26df5-112">Warunki wyścigu w konstruktorach</span><span class="sxs-lookup"><span data-stu-id="26df5-112">Race Conditions in Constructors</span></span>  
 <span data-ttu-id="26df5-113">W niektórych aplikacjach może być możliwe, aby inne wątki miały dostęp do elementów członkowskich klasy, zanim ich konstruktory klas zostały całkowicie uruchomione.</span><span class="sxs-lookup"><span data-stu-id="26df5-113">In some applications, it might be possible for other threads to access class members before their class constructors have completely run.</span></span> <span data-ttu-id="26df5-114">Należy przejrzeć wszystkie konstruktory klas, aby upewnić się, że nie występują problemy z zabezpieczeniami, jeśli taka sytuacja powinna mieć miejsce lub zsynchronizować wątki w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="26df5-114">You should review all class constructors to make sure that there are no security issues if this should happen, or synchronize threads if necessary.</span></span>  
  
## <a name="race-conditions-with-cached-objects"></a><span data-ttu-id="26df5-115">Warunki wyścigu z buforowanymi obiektami</span><span class="sxs-lookup"><span data-stu-id="26df5-115">Race Conditions with Cached Objects</span></span>  
 <span data-ttu-id="26df5-116">Kod, który buforuje informacje o zabezpieczeniach lub używa operacji [potwierdzenia](../../framework/misc/using-the-assert-method.md) zabezpieczeń dostępu kodu może być również narażony na sytuacje wyścigu, jeśli inne części klasy nie są odpowiednio zsynchronizowane, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="26df5-116">Code that caches security information or uses the code access security [Assert](../../framework/misc/using-the-assert-method.md) operation might also be vulnerable to race conditions if other parts of the class are not appropriately synchronized, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="26df5-117">Jeśli istnieją inne ścieżki do `DoOtherWork` , które mogą być wywoływane z innego wątku z tym samym obiektem, niezaufany obiekt wywołujący może przekroczyć żądanie.</span><span class="sxs-lookup"><span data-stu-id="26df5-117">If there are other paths to `DoOtherWork` that can be called from another thread with the same object, an untrusted caller can slip past a demand.</span></span>  
  
 <span data-ttu-id="26df5-118">Jeśli kod buforuje informacje o zabezpieczeniach, należy zapoznać się z informacjami dotyczącymi tej luki w zabezpieczeniach.</span><span class="sxs-lookup"><span data-stu-id="26df5-118">If your code caches security information, make sure that you review it for this vulnerability.</span></span>  
  
## <a name="race-conditions-in-finalizers"></a><span data-ttu-id="26df5-119">Sytuacje wyścigu w finalizatorach</span><span class="sxs-lookup"><span data-stu-id="26df5-119">Race Conditions in Finalizers</span></span>  
 <span data-ttu-id="26df5-120">Sytuacje wyścigu mogą również wystąpić w obiekcie, który odwołuje się do zasobu statycznego lub niezarządzanego, który następnie zwolni w jego finalizatorie.</span><span class="sxs-lookup"><span data-stu-id="26df5-120">Race conditions can also occur in an object that references a static or unmanaged resource that it then frees in its finalizer.</span></span> <span data-ttu-id="26df5-121">Jeśli wiele obiektów współużytkuje zasób, który jest manipulowany przez finalizator klasy, obiekty muszą zsynchronizować wszystkie dostęp do tego zasobu.</span><span class="sxs-lookup"><span data-stu-id="26df5-121">If multiple objects share a resource that is manipulated in a class's finalizer, the objects must synchronize all access to that resource.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26df5-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26df5-122">See also</span></span>

- [<span data-ttu-id="26df5-123">Wytyczne dotyczące bezpiecznego programowania</span><span class="sxs-lookup"><span data-stu-id="26df5-123">Secure Coding Guidelines</span></span>](secure-coding-guidelines.md)
