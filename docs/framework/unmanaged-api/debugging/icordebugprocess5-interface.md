---
title: ICorDebugProcess5 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5
helpviewer_keywords:
- ICorDebugProcess5 interface [.NET Framework debugging]
ms.assetid: 30a39d79-1f10-4328-9c5d-094ed824e2ba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e3aed85e989313e4778e12a6f6bb789ccef49747
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="fdd12-102">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="fdd12-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="fdd12-103">Umożliwia rozbudowywanie interfejsu ICorDebugProcess do obsługi dostępu do sterty zarządzanej, aby podać informacje o pamięci obiektów zarządzanych, oraz do ustalenia, czy debuger ładuje obrazów z pamięci podręcznej obrazów natywnych lokalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd12-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="fdd12-104">Metody</span><span class="sxs-lookup"><span data-stu-id="fdd12-104">Methods</span></span>  
  
|<span data-ttu-id="fdd12-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-105">Method</span></span>|<span data-ttu-id="fdd12-106">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd12-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="fdd12-107">EnableNGENPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="fdd12-108">Ustawia wartość określającą, jak ładowania obrazów natywnych podczas uruchamiania w debugerze zarządzanych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="fdd12-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="fdd12-109">EnumerateGCReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="fdd12-110">Pobiera moduł wyliczający dla wszystkich obiektów, które mają być zbierane pamięci w procesie.</span><span class="sxs-lookup"><span data-stu-id="fdd12-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="fdd12-111">EnumerateHandles, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="fdd12-112">Pobiera moduł wyliczający dla obiekt dojść w procesie.</span><span class="sxs-lookup"><span data-stu-id="fdd12-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="fdd12-113">EnumerateHeap, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="fdd12-114">Pobiera moduł wyliczający dla obiektów na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fdd12-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="fdd12-115">EnumerateHeapRegions, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="fdd12-116">Pobiera moduł wyliczający dla regionów sterty zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fdd12-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="fdd12-117">GetArrayLayout, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="fdd12-118">Pobiera informacje o układzie tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="fdd12-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="fdd12-119">GetGCHeapInformation, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="fdd12-120">Pobiera wskaźnik do [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) struktury, który zawiera informacje o obiektach, które mają być zbierane pamięci na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fdd12-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="fdd12-121">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="fdd12-122">Pobiera wskaźnik do obiektu na stercie zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="fdd12-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="fdd12-123">GetTypeFields, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="fdd12-124">Pobiera wskaźnik do tablicy, zawierający pola informacji dla typu na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="fdd12-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="fdd12-125">GetTypeForTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="fdd12-126">Pobiera obiekt typu, który dostarcza informacji na temat obiektu, w oparciu o ich identyfikatorów typu.</span><span class="sxs-lookup"><span data-stu-id="fdd12-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="fdd12-127">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="fdd12-128">Pobiera identyfikator typu dla obiektu pod określonym adresem.</span><span class="sxs-lookup"><span data-stu-id="fdd12-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="fdd12-129">GetTypeLayout, metoda</span><span class="sxs-lookup"><span data-stu-id="fdd12-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="fdd12-130">Pobiera informacje o układzie obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="fdd12-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd12-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdd12-131">Remarks</span></span>  
 <span data-ttu-id="fdd12-132">Ten interfejs logicznie rozszerza ICorDebugProcess, ICorDebugProcess2, i [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="fdd12-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fdd12-133">Ten interfejs nie obsługuje wywoływany zdalnie z innego komputera lub od innego procesu.</span><span class="sxs-lookup"><span data-stu-id="fdd12-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd12-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdd12-134">Requirements</span></span>  
 <span data-ttu-id="fdd12-135">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd12-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd12-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdd12-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdd12-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdd12-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdd12-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd12-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd12-139">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdd12-139">See Also</span></span>  
 [<span data-ttu-id="fdd12-140">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="fdd12-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="fdd12-141">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="fdd12-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
