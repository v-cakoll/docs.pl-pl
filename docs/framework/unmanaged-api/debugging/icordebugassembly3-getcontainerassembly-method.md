---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e4cda67145a0e624f87e93cf02ebdb6bc77c34d2
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69987602"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="8391a-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="8391a-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="8391a-103">Zwraca zestaw kontenerów tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="8391a-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8391a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8391a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8391a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8391a-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="8391a-106">Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw kontenerów, lub **wartość null** , jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="8391a-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="8391a-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="8391a-107">Return Value</span></span>  
 <span data-ttu-id="8391a-108">`S_OK`Jeśli wywołanie metody powiodło się; w przeciwnym razie, `ppAssembly` i ma **wartość null.** `S_FALSE`</span><span class="sxs-lookup"><span data-stu-id="8391a-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8391a-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8391a-109">Remarks</span></span>  
 <span data-ttu-id="8391a-110">Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów.</span><span class="sxs-lookup"><span data-stu-id="8391a-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="8391a-111">Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="8391a-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8391a-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8391a-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8391a-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8391a-113">Requirements</span></span>  
 <span data-ttu-id="8391a-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8391a-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8391a-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8391a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8391a-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8391a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8391a-117">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8391a-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8391a-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8391a-118">See also</span></span>

- [<span data-ttu-id="8391a-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="8391a-119">ICorDebugAssembly3 Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugassembly3-interface.md)
- [<span data-ttu-id="8391a-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8391a-120">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
