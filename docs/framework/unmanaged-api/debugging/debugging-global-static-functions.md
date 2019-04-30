---
title: Debugowanie statycznych funkcji globalnych
ms.date: 03/30/2017
helpviewer_keywords:
- global static functions [.NET Framework debugging]
- debugging global static functions [.NET Framework]
- unmanaged global static functions [.NET Framework], debugging
ms.assetid: efc64414-77c3-48d0-881a-8594ed416aad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e2403d736d031aab52525fc12b5071e764a8bde1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698528"
---
# <a name="debugging-global-static-functions"></a><span data-ttu-id="0546b-102">Debugowanie statycznych funkcji globalnych</span><span class="sxs-lookup"><span data-stu-id="0546b-102">Debugging Global Static Functions</span></span>
<span data-ttu-id="0546b-103">W tej sekcji opisano niezarządzane statyczne funkcje globalne, które korzysta z interfejsu API debugowania.</span><span class="sxs-lookup"><span data-stu-id="0546b-103">This section describes the unmanaged global static functions that the debugging API uses.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0546b-104">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="0546b-104">In This Section</span></span>  
 [<span data-ttu-id="0546b-105">_EFN_GetManagedExcepStack, funkcja</span><span class="sxs-lookup"><span data-stu-id="0546b-105">_EFN_GetManagedExcepStack Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedexcepstack-function.md)  
 <span data-ttu-id="0546b-106">Podany adres obiektu zarządzanego wyjątku zwraca wersję ślad stosu zawarte wewnątrz ciągu.</span><span class="sxs-lookup"><span data-stu-id="0546b-106">Given a managed exception object address, returns a string version of the stack trace contained inside.</span></span>  
  
 [<span data-ttu-id="0546b-107">_EFN_GetManagedObjectFieldInfo, funkcja</span><span class="sxs-lookup"><span data-stu-id="0546b-107">_EFN_GetManagedObjectFieldInfo Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectfieldinfo-function.md)  
 <span data-ttu-id="0546b-108">Pobiera przesunięcie od początku obiektu, do pola i wartość do pola, używając wskaźnika udostępnionego obiektu i nazwy pola.</span><span class="sxs-lookup"><span data-stu-id="0546b-108">Gets the offset from the start of an object to a field and the field's value, using the provided object pointer and field name.</span></span>  
  
 [<span data-ttu-id="0546b-109">_EFN_GetManagedObjectName, funkcja</span><span class="sxs-lookup"><span data-stu-id="0546b-109">_EFN_GetManagedObjectName Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-getmanagedobjectname-function.md)  
 <span data-ttu-id="0546b-110">Pobiera nazwę typu za pomocą wskaźnika udostępnionego obiektu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0546b-110">Gets the name of a type by using the provided managed object pointer.</span></span>  
  
 [<span data-ttu-id="0546b-111">_EFN_StackTrace, funkcja</span><span class="sxs-lookup"><span data-stu-id="0546b-111">_EFN_StackTrace Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/efn-stacktrace-function.md)  
 <span data-ttu-id="0546b-112">Zawiera tekst reprezentujący śledzenia stosu z zarządzanego i tablicę `CONTEXT` rejestruje, jeden dla każdego przejścia między niezarządzane, a kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="0546b-112">Provides a text representation of a managed stack trace and an array of `CONTEXT` records, one for each transition between unmanaged and managed code.</span></span>  
  
 [<span data-ttu-id="0546b-113">CLRDataCreateInstance, funkcja</span><span class="sxs-lookup"><span data-stu-id="0546b-113">CLRDataCreateInstance Function</span></span>](../../../../docs/framework/unmanaged-api/debugging/clrdatacreateinstance-function.md)  
 <span data-ttu-id="0546b-114">Metoda wywoływana przez wspólnego języka wspólnego (CLR) usługi dostępu do danych można utworzyć obiektu określonego interfejsu dla procesu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0546b-114">Called by the common language runtime (CLR) data access services to create the specified interface object for the specified target process.</span></span>  
  
 [<span data-ttu-id="0546b-115">PFN_CLRDataCreateInstance, wskaźnik funkcji</span><span class="sxs-lookup"><span data-stu-id="0546b-115">PFN_CLRDataCreateInstance Function Pointer</span></span>](../../../../docs/framework/unmanaged-api/debugging/pfn-clrdatacreateinstance-function-pointer.md)  
 <span data-ttu-id="0546b-116">Wskazuje funkcję, która jest wywoływana przez danych CLR dostęp do usług, można utworzyć obiektu określonego interfejsu dla procesu określonego obiektu docelowego.</span><span class="sxs-lookup"><span data-stu-id="0546b-116">Points to a function that is called by the CLR data access services to create the specified interface object for the specified target process.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0546b-117">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="0546b-117">Related Sections</span></span>  
 [<span data-ttu-id="0546b-118">Klasy coclass debugowania</span><span class="sxs-lookup"><span data-stu-id="0546b-118">Debugging Coclasses</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
  
 [<span data-ttu-id="0546b-119">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0546b-119">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
  
 [<span data-ttu-id="0546b-120">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0546b-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
  
 [<span data-ttu-id="0546b-121">Struktury debugowania</span><span class="sxs-lookup"><span data-stu-id="0546b-121">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
