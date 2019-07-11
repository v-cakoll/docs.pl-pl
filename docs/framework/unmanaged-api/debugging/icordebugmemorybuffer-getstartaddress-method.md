---
title: Metoda ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9208d07b697c3bb8a99e13582eda70dcb8dd826b
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67752770"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="ad3ef-102">Metoda ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="ad3ef-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="ad3ef-103">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad3ef-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ad3ef-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ad3ef-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ad3ef-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ad3ef-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="ad3ef-106">[out] Wskaźnik do adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="ad3ef-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ad3ef-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ad3ef-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="ad3ef-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="ad3ef-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ad3ef-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ad3ef-109">Requirements</span></span>  
 <span data-ttu-id="ad3ef-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ad3ef-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ad3ef-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ad3ef-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ad3ef-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ad3ef-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ad3ef-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ad3ef-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ad3ef-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ad3ef-114">See also</span></span>

- [<span data-ttu-id="ad3ef-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="ad3ef-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="ad3ef-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ad3ef-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
