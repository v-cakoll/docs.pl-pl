---
title: Metoda ICorDebugAssembly3::GetContainerAssembly
ms.date: 03/30/2017
ms.assetid: f5fddeb6-b82e-4ebb-b432-849ce8513c77
ms.openlocfilehash: 969cca6d5613670fc4b26fc973785b4874c3684c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778071"
---
# <a name="icordebugassembly3getcontainerassembly-method"></a><span data-ttu-id="09c03-102">Metoda ICorDebugAssembly3::GetContainerAssembly</span><span class="sxs-lookup"><span data-stu-id="09c03-102">ICorDebugAssembly3::GetContainerAssembly Method</span></span>
<span data-ttu-id="09c03-103">Zwraca zestaw kontenerów tego obiektu `ICorDebugAssembly3`.</span><span class="sxs-lookup"><span data-stu-id="09c03-103">Returns the container assembly of this `ICorDebugAssembly3` object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09c03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="09c03-104">Syntax</span></span>  
  
```cpp  
HRESULT GetContainerAssembly(  
    ICorDebugAssembly **ppAssembly  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="09c03-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="09c03-105">Parameters</span></span>  
 `ppAssembly`  
 <span data-ttu-id="09c03-106">Wskaźnik do adresu obiektu ICorDebugAssembly, który reprezentuje zestaw kontenerów, lub **wartość null** , jeśli wywołanie metody nie powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="09c03-106">A pointer to the address of an ICorDebugAssembly object that represents the container assembly, or **null** if the method call fails.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09c03-107">Wartość zwrócona</span><span class="sxs-lookup"><span data-stu-id="09c03-107">Return Value</span></span>  
 <span data-ttu-id="09c03-108">`S_OK`, jeśli wywołanie metody powiodło się; w przeciwnym razie `S_FALSE`i `ppAssembly` ma **wartość null**.</span><span class="sxs-lookup"><span data-stu-id="09c03-108">`S_OK` if the method call succeeds; otherwise, `S_FALSE`, and `ppAssembly` is **null**.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="09c03-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="09c03-109">Remarks</span></span>  
 <span data-ttu-id="09c03-110">Jeśli ten zestaw został scalony z innymi wewnątrz jednego zestawu kontenerów, Metoda ta zwraca zestaw kontenerów.</span><span class="sxs-lookup"><span data-stu-id="09c03-110">If this assembly has been merged with others inside a single container assembly, this method returns the container assembly.</span></span> <span data-ttu-id="09c03-111">Aby uzyskać więcej informacji i terminologii, zobacz temat [Metoda ICorDebugProcess6:: EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) .</span><span class="sxs-lookup"><span data-stu-id="09c03-111">For more information and terminology, see the [ICorDebugProcess6::EnableVirtualModuleSplitting](icordebugprocess6-enablevirtualmodulesplitting-method.md) topic.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="09c03-112">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="09c03-112">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09c03-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="09c03-113">Requirements</span></span>  
 <span data-ttu-id="09c03-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="09c03-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="09c03-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="09c03-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="09c03-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="09c03-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="09c03-117">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="09c03-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c03-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="09c03-118">See also</span></span>

- [<span data-ttu-id="09c03-119">ICorDebugAssembly3, interfejs</span><span class="sxs-lookup"><span data-stu-id="09c03-119">ICorDebugAssembly3 Interface</span></span>](icordebugassembly3-interface.md)
- [<span data-ttu-id="09c03-120">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="09c03-120">Debugging Interfaces</span></span>](debugging-interfaces.md)
