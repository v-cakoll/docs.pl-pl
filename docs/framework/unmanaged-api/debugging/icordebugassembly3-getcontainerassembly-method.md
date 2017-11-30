---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f9a32520c2a67c0bc51a3f88e9822db49e4a3974
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="031bc-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="031bc-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="031bc-103">Zwraca zestaw kontenera tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="031bc-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="031bc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="031bc-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="031bc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="031bc-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="031bc-106">Wskaźnik do adresu ICorDebugAssembly obiekt, który reprezentuje zestaw kontenera lub **null** Jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="031bc-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="031bc-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="031bc-107">Return Value</span></span>  
 <span data-ttu-id="031bc-108">`S_OK`Jeśli wywołanie metody zakończy się pomyślnie; w przeciwnym razie `S_FALSE`, i `ppAssembly` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="031bc-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="031bc-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="031bc-109">Remarks</span></span>  
 <span data-ttu-id="031bc-110">Jeśli ten zestaw został scalony z innymi wewnątrz zestawu jeden kontener, ta metoda zwraca zestawu kontenera.</span><span class="sxs-lookup"><span data-stu-id="031bc-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="031bc-111">Aby uzyskać więcej informacji oraz terminologii, zobacz [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="031bc-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="031bc-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="031bc-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="031bc-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="031bc-113">Requirements</span></span>  
 <span data-ttu-id="031bc-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="031bc-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="031bc-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="031bc-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="031bc-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="031bc-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="031bc-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="031bc-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="031bc-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="031bc-118">See Also</span></span>  
 [<span data-ttu-id="031bc-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="031bc-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="031bc-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="031bc-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
