---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b927d065f26a13d496aec8cd6c8cbc69cf3a8bc9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="917bd-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="917bd-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="917bd-103">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="917bd-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="917bd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="917bd-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="917bd-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="917bd-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="917bd-106">[out] Wskaźnik do adresu ICorDebugAssemblyEnum obiektu interfejsu, który moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="917bd-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="917bd-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="917bd-107">Return Value</span></span>  
 <span data-ttu-id="917bd-108">`S_OK`Jeśli `ICorDebugAssembly3` obiektu jest kontenerem; w przeciwnym razie `S_FALSE`, a wyliczenie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="917bd-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="917bd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="917bd-109">Remarks</span></span>  
 <span data-ttu-id="917bd-110">Symbole są wymagane do wyliczenia zawartych w niej zestawów.</span><span class="sxs-lookup"><span data-stu-id="917bd-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="917bd-111">Jeśli nie są obecne, metoda zwraca `S_FALSE`, i nie prawidłowym modułem wyliczającym jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="917bd-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="917bd-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="917bd-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="917bd-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="917bd-113">Requirements</span></span>  
 <span data-ttu-id="917bd-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="917bd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="917bd-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="917bd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="917bd-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="917bd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="917bd-117">**Wersje programu .NET framework:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="917bd-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="917bd-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="917bd-118">See Also</span></span>  
 [<span data-ttu-id="917bd-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="917bd-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="917bd-120">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="917bd-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
