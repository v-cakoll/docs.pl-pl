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
ms.openlocfilehash: b5904083be66d4bd6dc69729bebc28db8a800e77
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089241"
---
# <a name="icordebugprocess5-interface"></a><span data-ttu-id="55c76-102">ICorDebugProcess5 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="55c76-102">ICorDebugProcess5 Interface</span></span>
<span data-ttu-id="55c76-103">Rozszerza icordebugprocess — interfejs do obsługi dostępu do zarządzanej sterty, do dostarczania informacji dotyczących wyrzucania elementów bezużytecznych obiektów zarządzanych, a do określenia, czy debuger wczytuje obrazy z pamięci podręcznej obrazów natywnych lokalnej aplikacji.</span><span class="sxs-lookup"><span data-stu-id="55c76-103">Extends the ICorDebugProcess interface to support access to the managed heap, to provide information about garbage collection of managed objects, and to determine whether a debugger loads images from the application local native image cache.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="55c76-104">Metody</span><span class="sxs-lookup"><span data-stu-id="55c76-104">Methods</span></span>  
  
|<span data-ttu-id="55c76-105">Metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-105">Method</span></span>|<span data-ttu-id="55c76-106">Opis</span><span class="sxs-lookup"><span data-stu-id="55c76-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="55c76-107">EnableNGENPolicy, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-107">EnableNGenPolicy Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enablengenpolicy-method.md)|<span data-ttu-id="55c76-108">Ustawia wartość określającą, jak aplikacja ładuje obrazy natywne podczas uruchamiania w debugerze zarządzanych.</span><span class="sxs-lookup"><span data-stu-id="55c76-108">Sets a value that determines how an application loads native images while running under a managed debugger.</span></span>|  
|[<span data-ttu-id="55c76-109">EnumerateGCReferences, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-109">EnumerateGCReferences Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md)|<span data-ttu-id="55c76-110">Pobiera moduł wyliczający dla wszystkich obiektów, które mają być jesdnostką zbierającą śmieci w procesie.</span><span class="sxs-lookup"><span data-stu-id="55c76-110">Gets an enumerator for all objects that are to be garbage-collected in a process.</span></span>|  
|[<span data-ttu-id="55c76-111">EnumerateHandles, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-111">EnumerateHandles Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md)|<span data-ttu-id="55c76-112">Pobiera moduł wyliczający dla obiektu uchwytów w procesie.</span><span class="sxs-lookup"><span data-stu-id="55c76-112">Gets an enumerator for object handles in a process.</span></span>|  
|[<span data-ttu-id="55c76-113">EnumerateHeap, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-113">EnumerateHeap Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md)|<span data-ttu-id="55c76-114">Pobiera moduł wyliczający dla obiektów na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="55c76-114">Gets an enumerator for objects on the managed heap.</span></span>|  
|[<span data-ttu-id="55c76-115">EnumerateHeapRegions, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-115">EnumerateHeapRegions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheapregions-method.md)|<span data-ttu-id="55c76-116">Pobiera moduł wyliczający dla regionów zarządzanego stosu.</span><span class="sxs-lookup"><span data-stu-id="55c76-116">Gets an enumerator for regions of the managed heap.</span></span>|  
|[<span data-ttu-id="55c76-117">GetArrayLayout, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-117">GetArrayLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md)|<span data-ttu-id="55c76-118">Pobiera informacje o układ tablicy w pamięci.</span><span class="sxs-lookup"><span data-stu-id="55c76-118">Gets information about the layout of an array in memory.</span></span>|  
|[<span data-ttu-id="55c76-119">GetGCHeapInformation, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-119">GetGCHeapInformation Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getgcheapinformation-method.md)|<span data-ttu-id="55c76-120">Pobiera wskaźnik do [cor_heapinfo —](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) strukturę, która zawiera informacje o obiektach, które mają być jesdnostką zbierającą śmieci na stosie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="55c76-120">Gets a pointer to a [COR_HEAPINFO](../../../../docs/framework/unmanaged-api/debugging/cor-heapinfo-structure.md) structure that contains information about objects that are to be garbage-collected on the managed heap.</span></span>|  
|[<span data-ttu-id="55c76-121">GetObject, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-121">GetObject Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md)|<span data-ttu-id="55c76-122">Pobiera wskaźnik do obiektu w zarządzanym stosie.</span><span class="sxs-lookup"><span data-stu-id="55c76-122">Gets a pointer to an object on the managed heap.</span></span>|  
|[<span data-ttu-id="55c76-123">GetTypeFields, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-123">GetTypeFields Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md)|<span data-ttu-id="55c76-124">Pobiera wskaźnik do tablicy, która zawiera informacje o polach typu na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="55c76-124">Gets a pointer to an array that contains field information for a type based on its type identifier.</span></span>|  
|[<span data-ttu-id="55c76-125">GetTypeForTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-125">GetTypeForTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md)|<span data-ttu-id="55c76-126">Pobiera obiekt typu, który zawiera informacje dotyczące obiektu, w oparciu o ich identyfikatory typów.</span><span class="sxs-lookup"><span data-stu-id="55c76-126">Gets a type object that provides information about an object based on its type identifiers.</span></span>|  
|[<span data-ttu-id="55c76-127">GetTypeID, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-127">GetTypeID Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypeid-method.md)|<span data-ttu-id="55c76-128">Pobiera identyfikator typu obiektu pod podanym adresem.</span><span class="sxs-lookup"><span data-stu-id="55c76-128">Gets the type identifier for the object at a specified address.</span></span>|  
|[<span data-ttu-id="55c76-129">GetTypeLayout, metoda</span><span class="sxs-lookup"><span data-stu-id="55c76-129">GetTypeLayout Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypelayout-method.md)|<span data-ttu-id="55c76-130">Pobiera informacje o układ obiektu w pamięci na podstawie jego identyfikatora typu.</span><span class="sxs-lookup"><span data-stu-id="55c76-130">Gets information about the layout of an object in memory based on its type identifier.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="55c76-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="55c76-131">Remarks</span></span>  
 <span data-ttu-id="55c76-132">Ten interfejs rozszerza logicznie ICorDebugProcess, ICorDebugProcess2, i [icordebugprocess3 —](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfejsów.</span><span class="sxs-lookup"><span data-stu-id="55c76-132">This interface logically extends the ICorDebugProcess, ICorDebugProcess2, and [ICorDebugProcess3](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess3-interface.md) interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55c76-133">Ten interfejs może być wywoływany zdalnie z innego komputera lub od innego procesu.</span><span class="sxs-lookup"><span data-stu-id="55c76-133">This interface does not support being called remotely, either from another machine or from another process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="55c76-134">Wymagania</span><span class="sxs-lookup"><span data-stu-id="55c76-134">Requirements</span></span>  
 <span data-ttu-id="55c76-135">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="55c76-135">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="55c76-136">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="55c76-136">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="55c76-137">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="55c76-137">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="55c76-138">**Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="55c76-138">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="55c76-139">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55c76-139">See also</span></span>

- [<span data-ttu-id="55c76-140">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="55c76-140">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="55c76-141">Debugowanie</span><span class="sxs-lookup"><span data-stu-id="55c76-141">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
