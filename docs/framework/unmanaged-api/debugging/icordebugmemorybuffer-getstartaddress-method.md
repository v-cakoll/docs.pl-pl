---
title: Metoda ICorDebugMemoryBuffer::GetStartAddress
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 58649a0fc12ce63a1307af5d831dbf5e0d5a776a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59136984"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="3c8ce-102">Metoda ICorDebugMemoryBuffer::GetStartAddress</span><span class="sxs-lookup"><span data-stu-id="3c8ce-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="3c8ce-103">Pobiera adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="3c8ce-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3c8ce-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3c8ce-104">Syntax</span></span>  
  
```  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3c8ce-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3c8ce-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="3c8ce-106">[out] Wskaźnik do adres początkowy bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="3c8ce-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3c8ce-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3c8ce-107">Remarks</span></span>  
  
> [!WARNING]
>  <span data-ttu-id="3c8ce-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="3c8ce-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3c8ce-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3c8ce-109">Requirements</span></span>  
 <span data-ttu-id="3c8ce-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3c8ce-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3c8ce-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3c8ce-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3c8ce-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3c8ce-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3c8ce-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3c8ce-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3c8ce-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3c8ce-114">See also</span></span>

- [<span data-ttu-id="3c8ce-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="3c8ce-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="3c8ce-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3c8ce-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
