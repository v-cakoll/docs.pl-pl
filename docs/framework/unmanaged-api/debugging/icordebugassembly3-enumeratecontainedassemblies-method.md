---
title: Metoda ICorDebugAssembly3::EnumerateContainedAssemblies
ms.date: 03/30/2017
ms.assetid: 98f15b05-afad-4616-9e2a-1a9af31948b6
ms.openlocfilehash: 032f32a08efa92cea682b0e2fc974dc607a9dca4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133943"
---
# <a name="icordebugassembly3enumeratecontainedassemblies-method"></a><span data-ttu-id="01d70-102">Metoda ICorDebugAssembly3::EnumerateContainedAssemblies</span><span class="sxs-lookup"><span data-stu-id="01d70-102">ICorDebugAssembly3::EnumerateContainedAssemblies Method</span></span>
<span data-ttu-id="01d70-103">Pobiera moduł wyliczający dla zestawów zawartych w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="01d70-103">Gets an enumerator for the assemblies contained in this assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01d70-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="01d70-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateContainedAssemblies(  
    ICorDebugAssemblyEnum **ppAssemblies  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="01d70-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="01d70-105">Parameters</span></span>  
 `ppAssemblies`  
 <span data-ttu-id="01d70-106">określoną Wskaźnik do adresu obiektu interfejsu ICorDebugAssemblyEnum, który jest modułem wyliczającym.</span><span class="sxs-lookup"><span data-stu-id="01d70-106">[out] A pointer to the address of an ICorDebugAssemblyEnum interface object that is the enumerator.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="01d70-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="01d70-107">Return Value</span></span>  
 <span data-ttu-id="01d70-108">`S_OK`, jeśli ten obiekt `ICorDebugAssembly3` jest kontenerem; w przeciwnym razie `S_FALSE`i Wyliczenie jest puste.</span><span class="sxs-lookup"><span data-stu-id="01d70-108">`S_OK` if this `ICorDebugAssembly3` object is a container; otherwise, `S_FALSE`, and the enumeration is empty.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="01d70-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="01d70-109">Remarks</span></span>  
 <span data-ttu-id="01d70-110">Symbole są konieczne do wyliczenia zawartych zestawów.</span><span class="sxs-lookup"><span data-stu-id="01d70-110">Symbols are needed to enumerate the contained assemblies.</span></span> <span data-ttu-id="01d70-111">Jeśli nie są one obecne, metoda zwraca `S_FALSE`i nie podano prawidłowego modułu wyliczającego.</span><span class="sxs-lookup"><span data-stu-id="01d70-111">If they aren't present, the method returns `S_FALSE`, and no valid enumerator is provided.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="01d70-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="01d70-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="01d70-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="01d70-113">Requirements</span></span>  
 <span data-ttu-id="01d70-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="01d70-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="01d70-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="01d70-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="01d70-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="01d70-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="01d70-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="01d70-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="01d70-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="01d70-118">See also</span></span>

- [<span data-ttu-id="01d70-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="01d70-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="01d70-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="01d70-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
