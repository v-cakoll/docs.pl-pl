---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54ccb52468a530280527252e0e0c43cc9edbb2c3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59080959"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="1a93c-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="1a93c-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="1a93c-103">Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="1a93c-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1a93c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1a93c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="1a93c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="1a93c-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="1a93c-106">[out] Wskaźnik na adres icordebugassemblyenum — interfejs obiekt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="1a93c-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1a93c-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="1a93c-107">Return Value</span></span>  
 <span data-ttu-id="1a93c-108">`S_OK` Jeśli ten `ICorDebugAssembly3` obiekt to kontener, a w przeciwnym razie `S_FALSE`, i wyliczenia jest pusty.</span><span class="sxs-lookup"><span data-stu-id="1a93c-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1a93c-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1a93c-109">Remarks</span></span>  
 <span data-ttu-id="1a93c-110">Symbole są wymagane do wyliczenia zawarte zestawów.</span><span class="sxs-lookup"><span data-stu-id="1a93c-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="1a93c-111">Jeśli nie są obecne, metoda zwraca `S_FALSE`, i jest dostępne nie prawidłowym modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="1a93c-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1a93c-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="1a93c-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1a93c-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1a93c-113">Requirements</span></span>  
 <span data-ttu-id="1a93c-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1a93c-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1a93c-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1a93c-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1a93c-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1a93c-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1a93c-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1a93c-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a93c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1a93c-118">See also</span></span>

- [<span data-ttu-id="1a93c-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="1a93c-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="1a93c-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="1a93c-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
