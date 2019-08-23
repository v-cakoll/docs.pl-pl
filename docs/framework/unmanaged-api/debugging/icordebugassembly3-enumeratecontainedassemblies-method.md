---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9120119056fda3f16b4a0bf8bad839b74463d633
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959342"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="c6695-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="c6695-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="c6695-103">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="c6695-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6695-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c6695-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c6695-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c6695-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="c6695-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugAssemblyEnum, który jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="c6695-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6695-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="c6695-107">Return Value</span></span>  
 <span data-ttu-id="c6695-108">`S_OK`Jeśli ten `ICorDebugAssembly3` obiekt jest kontenerem; `S_FALSE`w przeciwnym razie, a Wyliczenie jest puste.</span><span class="sxs-lookup"><span data-stu-id="c6695-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c6695-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6695-109">Remarks</span></span>  
 <span data-ttu-id="c6695-110">Symbole są konieczne do wyliczenia zawartych zestawów.</span><span class="sxs-lookup"><span data-stu-id="c6695-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="c6695-111">Jeśli ich nie ma, metoda zwraca `S_FALSE`i nie podano prawidłowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="c6695-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6695-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="c6695-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6695-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c6695-113">Requirements</span></span>  
 <span data-ttu-id="c6695-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c6695-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c6695-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c6695-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c6695-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c6695-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c6695-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c6695-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6695-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6695-118">See also</span></span>

- [<span data-ttu-id="c6695-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="c6695-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="c6695-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="c6695-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
