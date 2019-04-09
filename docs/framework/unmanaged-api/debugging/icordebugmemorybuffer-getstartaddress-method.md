---
title: Metoda ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136984"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="33f2a-102">Metoda ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="33f2a-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="33f2a-103">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="33f2a-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33f2a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33f2a-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="33f2a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33f2a-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="33f2a-106">[out] Wskaźnik do adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="33f2a-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="33f2a-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="33f2a-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="33f2a-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="33f2a-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33f2a-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33f2a-109">Requirements</span></span>  
 <span data-ttu-id="33f2a-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33f2a-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33f2a-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33f2a-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33f2a-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33f2a-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="33f2a-113">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="33f2a-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33f2a-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33f2a-114">See also</span></span>

- [<span data-ttu-id="33f2a-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="33f2a-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="33f2a-116">Debugowanie — Interfejsy</span><span class="sxs-lookup"><span data-stu-id="33f2a-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
