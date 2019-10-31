---
title: Debugowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
ms.openlocfilehash: 965724c1e937fa62f05c33b0dcf8a5c8b9e1b029
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124319"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="522da-102">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="522da-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="522da-103">W tej sekcji opisano niezarządzane globalne funkcje statyczne używane przez interfejs API debugowania.</span><span class="sxs-lookup"><span data-stu-id="522da-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="522da-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="522da-104">In This Section</span></span>  
 [<span data-ttu-id="522da-105">_EFN_GetManagedExcepStack, funkcja</span><span class="sxs-lookup"><span data-stu-id="522da-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="522da-106">Dany adres obiektu wyjątku zarządzanego zwraca wersję ciągu śledzenia stosu zawartych wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="522da-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="522da-107">_EFN_GetManagedObjectFieldInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="522da-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="522da-108">Pobiera przesunięcie od początku obiektu do pola i wartości pola przy użyciu podanego wskaźnika obiektu i nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="522da-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="522da-109">_EFN_GetManagedObjectName, funkcja</span><span class="sxs-lookup"><span data-stu-id="522da-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="522da-110">Pobiera nazwę typu za pomocą podanego wskaźnika obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="522da-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="522da-111">_EFN_StackTrace, funkcja</span><span class="sxs-lookup"><span data-stu-id="522da-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="522da-112">Przedstawia tekstową reprezentację zarządzanego śledzenia stosu i tablicę `CONTEXT` rekordów, po jednym dla każdego przejścia między niezarządzanym i zarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="522da-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="522da-113">CLRDataCreateInstance, funkcja</span><span class="sxs-lookup"><span data-stu-id="522da-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="522da-114">Wywoływane przez usługi dostępu do danych środowiska uruchomieniowego języka wspólnego (CLR) w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="522da-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="522da-115">PFN_CLRDataCreateInstance, wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="522da-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="522da-116">Wskazuje funkcję, która jest wywoływana przez usługi dostępu do danych CLR w celu utworzenia określonego obiektu interfejsu dla określonego procesu docelowego.</span><span class="sxs-lookup"><span data-stu-id="522da-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="522da-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="522da-117">Related Sections</span></span>  
 [<span data-ttu-id="522da-118">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="522da-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="522da-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="522da-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="522da-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="522da-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="522da-121">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="522da-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
