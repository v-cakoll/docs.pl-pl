---
title: 'ICorDebugMemoryBuffer:: GetStartAddress, Metoda'
ms.date: 03/30/2017
ms.assetid: f804d9ab-8c88-44f0-b278-5fcca7f87726
ms.openlocfilehash: f2b09c847a6bf577b78c8155f85f07b93877fbe9
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793169"
---
# <a name="icordebugmemorybuffergetstartaddress-method"></a><span data-ttu-id="6d07c-102">ICorDebugMemoryBuffer:: GetStartAddress, Metoda</span><span class="sxs-lookup"><span data-stu-id="6d07c-102">ICorDebugMemoryBuffer::GetStartAddress Method</span></span>
<span data-ttu-id="6d07c-103">Pobiera początkowy adres bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d07c-103">Gets the starting address of the memory buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d07c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6d07c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetStartAddress(  
   [out] LPCVOID *address  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6d07c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6d07c-105">Parameters</span></span>  
 `address`  
 <span data-ttu-id="6d07c-106">określoną Wskaźnik do adresu początkowego bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="6d07c-106">[out] A pointer to the starting address of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6d07c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6d07c-107">Remarks</span></span>  
  
> [!WARNING]
> <span data-ttu-id="6d07c-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="6d07c-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6d07c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6d07c-109">Requirements</span></span>  
 <span data-ttu-id="6d07c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6d07c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6d07c-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6d07c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6d07c-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6d07c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6d07c-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6d07c-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d07c-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6d07c-114">See also</span></span>

- [<span data-ttu-id="6d07c-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="6d07c-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="6d07c-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="6d07c-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
