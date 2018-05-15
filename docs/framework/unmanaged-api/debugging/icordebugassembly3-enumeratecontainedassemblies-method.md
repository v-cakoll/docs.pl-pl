---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb84efe78568bbae03f76efc456fc8ae605e4db9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="4467c-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="4467c-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="4467c-103">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="4467c-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4467c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4467c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="4467c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4467c-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="4467c-106">[out] Wskaźnik do adresu ICorDebugAssemblyEnum obiektu interfejsu, który moduł wyliczający.</span><span class="sxs-lookup"><span data-stu-id="4467c-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4467c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="4467c-107">Return Value</span></span>  
 <span data-ttu-id="4467c-108">`S_OK` Jeśli `ICorDebugAssembly3` obiektu jest kontenerem; w przeciwnym razie `S_FALSE`, a wyliczenie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="4467c-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4467c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4467c-109">Remarks</span></span>  
 <span data-ttu-id="4467c-110">Symbole są wymagane do wyliczenia zawartych w niej zestawów.</span><span class="sxs-lookup"><span data-stu-id="4467c-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="4467c-111">Jeśli nie są obecne, metoda zwraca `S_FALSE`, i nie prawidłowym modułem wyliczającym jest dostępne.</span><span class="sxs-lookup"><span data-stu-id="4467c-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4467c-112">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="4467c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4467c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4467c-113">Requirements</span></span>  
 <span data-ttu-id="4467c-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4467c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4467c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="4467c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4467c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4467c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4467c-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4467c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4467c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4467c-118">See Also</span></span>  
 [<span data-ttu-id="4467c-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="4467c-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)  
 [<span data-ttu-id="4467c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="4467c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
