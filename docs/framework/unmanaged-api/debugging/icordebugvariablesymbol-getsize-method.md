---
title: 'ICorDebugVariableSymbol:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: add0cd9d-9a29-49b1-ae07-d9d3786b4ccd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 782073968030d3dcdbbe49e0ed7732fe15c4a3bb
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968165"
---
# <a name="icordebugvariablesymbolgetsize-method"></a><span data-ttu-id="7238b-102">ICorDebugVariableSymbol:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="7238b-102">ICorDebugVariableSymbol::GetSize Method</span></span>
<span data-ttu-id="7238b-103">Pobiera rozmiar zmiennej w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7238b-103">Gets the size of a variable in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7238b-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7238b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbValue  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7238b-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7238b-105">Parameters</span></span>  
 `pcbValue`  
 <span data-ttu-id="7238b-106">Wskaźnik do 32-bitowej liczby całkowitej bez znaku zawierającego rozmiar zmiennej.</span><span class="sxs-lookup"><span data-stu-id="7238b-106">A pointer to a 32-bit unsigned integer containing the size of the variable.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7238b-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7238b-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7238b-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7238b-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7238b-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7238b-109">Requirements</span></span>  
 <span data-ttu-id="7238b-110">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7238b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7238b-111">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7238b-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7238b-112">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7238b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7238b-113">**.NET Framework wersje:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7238b-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7238b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7238b-114">See also</span></span>

- [<span data-ttu-id="7238b-115">ICorDebugVariableSymbol, interfejs</span><span class="sxs-lookup"><span data-stu-id="7238b-115">ICorDebugVariableSymbol Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [<span data-ttu-id="7238b-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7238b-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
