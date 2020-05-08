---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 068a08d70f2443edfe0970ec1ffb8cba9953c6b9
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894851"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="93d83-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="93d83-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="93d83-103">Zwraca zestaw kontenerów tego `ICorDebugAssembly3` obiektu.</span><span class="sxs-lookup"><span data-stu-id="93d83-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93d83-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93d83-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="93d83-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="93d83-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="93d83-106">Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw kontenerów, lub **wartość null** , jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="93d83-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="93d83-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="93d83-107">Return Value</span></span>  
 <span data-ttu-id="93d83-108">`S_OK`Jeśli wywołanie metody powiodło się; `S_FALSE`w przeciwnym razie, `ppAssembly` i ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="93d83-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="93d83-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="93d83-109">Remarks</span></span>  
 <span data-ttu-id="93d83-110">Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów.</span><span class="sxs-lookup"><span data-stu-id="93d83-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="93d83-111">Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="93d83-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="93d83-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="93d83-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="93d83-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93d83-113">Requirements</span></span>  
 <span data-ttu-id="93d83-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93d83-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93d83-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93d83-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93d83-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93d83-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93d83-117">**.NET Framework wersje:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93d83-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93d83-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="93d83-118">See also</span></span>

- [<span data-ttu-id="93d83-119">Interfejs ICorDebugAssembly3</span><span class="sxs-lookup"><span data-stu-id="93d83-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="93d83-120">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="93d83-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
