---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acb34ac2568ac88797441306820e6e762b5ac46e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33409730"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="bc1d5-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="bc1d5-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="bc1d5-103">Zwraca zestaw kontenera tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc1d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="bc1d5-104">Syntax</span></span>  
  
```  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bc1d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="bc1d5-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="bc1d5-106">Wskaźnik do adresu ICorDebugAssembly obiekt, który reprezentuje zestaw kontenera lub **null** Jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bc1d5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="bc1d5-107">Return Value</span></span>  
 <span data-ttu-id="bc1d5-108">`S_OK` Jeśli wywołanie metody zakończy się pomyślnie; w przeciwnym razie `S_FALSE`, i `ppAssembly` jest **null**.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="bc1d5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bc1d5-109">Remarks</span></span>  
 <span data-ttu-id="bc1d5-110">Jeśli ten zestaw został scalony z innymi wewnątrz zestawu jeden kontener, ta metoda zwraca zestawu kontenera.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="bc1d5-111">Aby uzyskać więcej informacji oraz terminologii, zobacz [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) tematu.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bc1d5-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="bc1d5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bc1d5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bc1d5-113">Requirements</span></span>  
 <span data-ttu-id="bc1d5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bc1d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bc1d5-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bc1d5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bc1d5-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bc1d5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bc1d5-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bc1d5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1d5-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bc1d5-118">See Also</span></span>  
 [<span data-ttu-id="bc1d5-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="bc1d5-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="bc1d5-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="bc1d5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
