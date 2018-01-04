---
title: "Oczyszczanie zasobów niezarządzanych"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Close method
- Dispose method
- garbage collector
- garbage collection, unmanaged resources
- cleanup operations
- explicit cleanups
- unmanaged resource cleanup
- Finalize method
ms.assetid: a17b0066-71c2-4ba4-9822-8e19332fc213
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fea76042bb603889764a9d42b5a7836d704fcd48
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="cleaning-up-unmanaged-resources"></a><span data-ttu-id="fd718-102">Oczyszczanie zasobów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="fd718-102">Cleaning Up Unmanaged Resources</span></span>
<span data-ttu-id="fd718-103">W większości obiektów tworzonych przez aplikację może polegać na. Moduł zbierający elementy bezużyteczne w sieci do obsługi zarządzania pamięcią.</span><span class="sxs-lookup"><span data-stu-id="fd718-103">For the majority of the objects that your app creates, you can rely on .NET's garbage collector to handle memory management.</span></span> <span data-ttu-id="fd718-104">Jeśli jednak są tworzone obiekty zawierające niezarządzane zasoby, należy jawnie zwalniać te zasoby po zakończeniu używania ich w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fd718-104">However, when you create objects that include unmanaged resources, you must explicitly release those resources when you finish using them in your app.</span></span> <span data-ttu-id="fd718-105">Najpopularniejsze typy niezarządzanych zasobów to obiekty, które umieszczają w otoce zasoby systemu operacyjnego, takie jak pliki, okna, połączenia sieciowe lub połączenia bazy danych.</span><span class="sxs-lookup"><span data-stu-id="fd718-105">The most common types of unmanaged resource are objects that wrap operating system resources, such as files, windows, network connections, or database connections.</span></span> <span data-ttu-id="fd718-106">Mimo że moduł odśmiecania pamięci jest w stanie śledzić okres istnienia obiektu hermetyzującego niezarządzany zasób, nie ma informacji, jak zwolnić i wyczyścić niezarządzany zasób.</span><span class="sxs-lookup"><span data-stu-id="fd718-106">Although the garbage collector is able to track the lifetime of an object that encapsulates an unmanaged resource, it doesn't know how to release and clean up the unmanaged resource.</span></span>  
  
 <span data-ttu-id="fd718-107">Jeśli typy w aplikacji używają niezarządzanych zasobów, należny wykonać następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fd718-107">If your types use unmanaged resources, you should do the following:</span></span>  
  
-   <span data-ttu-id="fd718-108">Implementowanie [wzorzec dispose](../../../docs/standard/design-guidelines/dispose-pattern.md).</span><span class="sxs-lookup"><span data-stu-id="fd718-108">Implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md).</span></span> <span data-ttu-id="fd718-109">Wymaga to podania <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji, aby włączyć deterministyczne wersji zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="fd718-109">This requires that you provide an <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation to enable the deterministic release of  unmanaged resources.</span></span> <span data-ttu-id="fd718-110">Klient korzystający z wywołania typu <xref:System.IDisposable.Dispose%2A> po obiektu (i wykorzystuje zasoby) nie jest już potrzebne.</span><span class="sxs-lookup"><span data-stu-id="fd718-110">A consumer of your type calls <xref:System.IDisposable.Dispose%2A> when the object (and the resources it uses) is no longer needed.</span></span> <span data-ttu-id="fd718-111"><xref:System.IDisposable.Dispose%2A> Metody natychmiast zwalnia zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="fd718-111">The <xref:System.IDisposable.Dispose%2A> method immediately releases the unmanaged resources.</span></span>  
  
-   <span data-ttu-id="fd718-112">Przewidują niezarządzane zasoby do zwolnienia w przypadku, gdy klient tego typu zapomni do wywołania <xref:System.IDisposable.Dispose%2A>.</span><span class="sxs-lookup"><span data-stu-id="fd718-112">Provide for your unmanaged resources to be released in the event that a consumer of your type forgets to call <xref:System.IDisposable.Dispose%2A>.</span></span> <span data-ttu-id="fd718-113">Istnieją dwa sposoby wykonania tej czynności:</span><span class="sxs-lookup"><span data-stu-id="fd718-113">There are two ways to do this:</span></span>  
  
    -   <span data-ttu-id="fd718-114">Użycie bezpiecznego dojścia w celu umieszczenie niezarządzanego zasobu w otoce.</span><span class="sxs-lookup"><span data-stu-id="fd718-114">Use a safe handle to wrap your unmanaged resource.</span></span> <span data-ttu-id="fd718-115">Jest to zalecana technika.</span><span class="sxs-lookup"><span data-stu-id="fd718-115">This is the recommended technique.</span></span> <span data-ttu-id="fd718-116">Pochodne bezpiecznego dojścia <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> klasy i obejmują niezawodne <xref:System.Object.Finalize%2A> — metoda.</span><span class="sxs-lookup"><span data-stu-id="fd718-116">Safe handles are derived from the <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=nameWithType> class and include a robust <xref:System.Object.Finalize%2A> method.</span></span> <span data-ttu-id="fd718-117">Korzystając z bezpieczne dojście, po prostu zaimplementowaniem <xref:System.IDisposable> interfejsu i Wywołaj bezpieczne dojście <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> metody w Twojej <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementacji.</span><span class="sxs-lookup"><span data-stu-id="fd718-117">When you use a safe handle, you simply implement the <xref:System.IDisposable> interface and call your safe handle's <xref:System.Runtime.InteropServices.SafeHandle.Dispose%2A> method in your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation.</span></span> <span data-ttu-id="fd718-118">Bezpieczne dojście finalizatora jest wywoływana automatycznie przez moduł garbage collector jeśli jego <xref:System.IDisposable.Dispose%2A> nie jest wywoływana metoda.</span><span class="sxs-lookup"><span data-stu-id="fd718-118">The safe handle's finalizer is called automatically by the garbage collector if its <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>  
  
         <span data-ttu-id="fd718-119">—lub—</span><span class="sxs-lookup"><span data-stu-id="fd718-119">—or—</span></span>  
  
    -   <span data-ttu-id="fd718-120">Zastąpienie <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="fd718-120">Override the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="fd718-121">Finalizacji umożliwia deterministyczna wersji zasoby niezarządzane, gdy konsumenta typu nie można wywołać <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> do usuwania z nich w sposób niejednoznaczny.</span><span class="sxs-lookup"><span data-stu-id="fd718-121">Finalization enables the non-deterministic release of unmanaged resources when the consumer of a type fails to call <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> to dispose of them deterministically.</span></span> <span data-ttu-id="fd718-122">Jednak finalizacja obiektu może być złożoną i podatną na błędy operacją, więc zalecane jest używanie bezpiecznego dojścia, zamiast dostarczania własnego finalizatora.</span><span class="sxs-lookup"><span data-stu-id="fd718-122">However, because object finalization can be a complex and error-prone operation, we recommend that you use a safe handle instead of providing your own finalizer.</span></span>  
  
 <span data-ttu-id="fd718-123">Konsumenci tego typu można wywoływać z <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementację bezpośrednio, aby zwolnić pamięć, używany przez zasoby niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="fd718-123">Consumers of your type can then call your <xref:System.IDisposable.Dispose%2A?displayProperty=nameWithType> implementation directly to free memory used by unmanaged resources.</span></span> <span data-ttu-id="fd718-124">Gdy prawidłowo zaimplementować <xref:System.IDisposable.Dispose%2A> metody, albo bezpieczne dojście <xref:System.Object.Finalize%2A> metody lub zastąpienia z <xref:System.Object.Finalize%2A?displayProperty=nameWithType> metody staje się zabezpieczenia, aby wyczyścić zasoby w przypadku gdy <xref:System.IDisposable.Dispose%2A> nie wywołano metody.</span><span class="sxs-lookup"><span data-stu-id="fd718-124">When you properly implement a <xref:System.IDisposable.Dispose%2A> method, either your safe handle's <xref:System.Object.Finalize%2A> method or your own override of the <xref:System.Object.Finalize%2A?displayProperty=nameWithType> method becomes a safeguard to clean up resources in the event that the <xref:System.IDisposable.Dispose%2A> method is not called.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fd718-125">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fd718-125">In This Section</span></span>  
 [<span data-ttu-id="fd718-126">Implementacja metody Dispose</span><span class="sxs-lookup"><span data-stu-id="fd718-126">Implementing a Dispose Method</span></span>](../../../docs/standard/garbage-collection/implementing-dispose.md)  
 <span data-ttu-id="fd718-127">Opisuje sposób wdrożenia [wzorzec dispose](../../../docs/standard/design-guidelines/dispose-pattern.md) za zwolnienie niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fd718-127">Describes how to implement the [dispose pattern](../../../docs/standard/design-guidelines/dispose-pattern.md) for releasing unmanaged resources.</span></span>  
  
 [<span data-ttu-id="fd718-128">Używanie obiektów implementujących interfejs IDisposable</span><span class="sxs-lookup"><span data-stu-id="fd718-128">Using Objects That Implement IDisposable</span></span>](../../../docs/standard/garbage-collection/using-objects.md)  
 <span data-ttu-id="fd718-129">W tym artykule opisano, jak konsumentów typu upewnij się, że jego <xref:System.IDisposable.Dispose%2A> nosi nazwę wdrożenia.</span><span class="sxs-lookup"><span data-stu-id="fd718-129">Describes how consumers of a type ensure that its <xref:System.IDisposable.Dispose%2A> implementation is called.</span></span> <span data-ttu-id="fd718-130">Firma Microsoft zaleca używanie języka C# `using` instrukcji lub Visual Basic `Using` instrukcji w tym celu.</span><span class="sxs-lookup"><span data-stu-id="fd718-130">We recommend using the C# `using` statement or the Visual Basic `Using` statement to do this.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fd718-131">Tematy pomocy</span><span class="sxs-lookup"><span data-stu-id="fd718-131">Reference</span></span>  
 <xref:System.IDisposable?displayProperty=nameWithType>  
 <span data-ttu-id="fd718-132">Definiuje <xref:System.IDisposable.Dispose%2A> metoda zwalniania niezarządzanych zasobów.</span><span class="sxs-lookup"><span data-stu-id="fd718-132">Defines the <xref:System.IDisposable.Dispose%2A> method for releasing unmanaged resources.</span></span>  
  
 <xref:System.Object.Finalize%2A?displayProperty=nameWithType>  
 <span data-ttu-id="fd718-133">W przypadku niezarządzanych zasobów nie są wydawane przez zapewnia dla obiekt finalizacji <xref:System.IDisposable.Dispose%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fd718-133">Provides for object finalization if unmanaged resources are not released by the <xref:System.IDisposable.Dispose%2A> method.</span></span>  
  
 <xref:System.GC.SuppressFinalize%2A?displayProperty=nameWithType>  
 <span data-ttu-id="fd718-134">Pomija finalizację.</span><span class="sxs-lookup"><span data-stu-id="fd718-134">Suppresses finalization.</span></span> <span data-ttu-id="fd718-135">Ta metoda jest zazwyczaj wywoływana z `Dispose` metodę, aby zapobiec finalizator wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fd718-135">This method is customarily called from a `Dispose` method to prevent a finalizer from executing.</span></span>
