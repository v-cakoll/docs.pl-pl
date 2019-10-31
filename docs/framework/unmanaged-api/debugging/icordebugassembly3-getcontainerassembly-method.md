---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 39f8dd042ea785258dfe5c048ebc348852be6892
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73095392"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="3a8d5-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="3a8d5-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="3a8d5-103">Zwraca zestaw kontenerów tego obiektu `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="3a8d5-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a8d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3a8d5-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3a8d5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3a8d5-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="3a8d5-106">Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw kontenerów, lub **wartość null** , jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="3a8d5-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3a8d5-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3a8d5-107">Return Value</span></span>  
 <span data-ttu-id="3a8d5-108">`S_OK`, jeśli wywołanie metody powiodło się; w przeciwnym razie `S_FALSE`i `ppAssembly` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="3a8d5-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3a8d5-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3a8d5-109">Remarks</span></span>  
 <span data-ttu-id="3a8d5-110">Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów.</span><span class="sxs-lookup"><span data-stu-id="3a8d5-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="3a8d5-111">Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a8d5-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="3a8d5-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3a8d5-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3a8d5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3a8d5-113">Requirements</span></span>  
 <span data-ttu-id="3a8d5-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a8d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a8d5-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3a8d5-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3a8d5-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3a8d5-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a8d5-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a8d5-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a8d5-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3a8d5-118">See also</span></span>

- [<span data-ttu-id="3a8d5-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="3a8d5-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="3a8d5-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3a8d5-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
