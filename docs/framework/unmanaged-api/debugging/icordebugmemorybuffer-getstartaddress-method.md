---
title: Metoda ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f4f51c087112053aa7b76bff1f7c55016c8ff57
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57474751"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="27b55-102">Metoda ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="27b55-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="27b55-103">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="27b55-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27b55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="27b55-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="27b55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="27b55-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="27b55-106">[out] Wskaźnik do adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="27b55-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="27b55-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="27b55-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="27b55-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="27b55-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27b55-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="27b55-109">Requirements</span></span>  
 <span data-ttu-id="27b55-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="27b55-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="27b55-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="27b55-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="27b55-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="27b55-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="27b55-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="27b55-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27b55-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="27b55-114">See also</span></span>
- [<span data-ttu-id="27b55-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="27b55-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="27b55-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="27b55-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
