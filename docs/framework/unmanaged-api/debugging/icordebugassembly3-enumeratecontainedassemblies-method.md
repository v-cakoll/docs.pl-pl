---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05c4e2a5c16f11f80cc8356a65b746eab81a3899
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67744397"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="8aa35-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="8aa35-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="8aa35-103">Pobiera moduł wyliczający dla zestawów znajdujących się w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="8aa35-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8aa35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8aa35-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8aa35-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8aa35-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="8aa35-106">[out] Wskaźnik na adres icordebugassemblyenum — interfejs obiekt modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="8aa35-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8aa35-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8aa35-107">Return Value</span></span>  
 <span data-ttu-id="8aa35-108">`S_OK` Jeśli ten `ICorDebugAssembly3` obiekt to kontener, a w przeciwnym razie `S_FALSE`, i wyliczenia jest pusty.</span><span class="sxs-lookup"><span data-stu-id="8aa35-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8aa35-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8aa35-109">Remarks</span></span>  
 <span data-ttu-id="8aa35-110">Symbole są wymagane do wyliczenia zawarte zestawów.</span><span class="sxs-lookup"><span data-stu-id="8aa35-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="8aa35-111">Jeśli nie są obecne, metoda zwraca `S_FALSE`, i jest dostępne nie prawidłowym modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="8aa35-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8aa35-112">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8aa35-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8aa35-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8aa35-113">Requirements</span></span>  
 <span data-ttu-id="8aa35-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8aa35-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8aa35-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8aa35-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8aa35-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8aa35-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8aa35-117">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8aa35-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8aa35-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8aa35-118">See also</span></span>

- [<span data-ttu-id="8aa35-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="8aa35-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="8aa35-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8aa35-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
