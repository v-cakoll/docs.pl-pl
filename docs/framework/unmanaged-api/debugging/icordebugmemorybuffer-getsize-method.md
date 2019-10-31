---
title: 'ICorDebugMemoryBuffer:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 1693860abe99884ee443be0666dfb6b485a219a0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73128006"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="7da2e-102">ICorDebugMemoryBuffer:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="7da2e-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="7da2e-103">Pobiera rozmiar buforu pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="7da2e-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7da2e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7da2e-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7da2e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="7da2e-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="7da2e-106">określoną Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="7da2e-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7da2e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7da2e-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7da2e-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="7da2e-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7da2e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7da2e-109">Requirements</span></span>  
 <span data-ttu-id="7da2e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7da2e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7da2e-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="7da2e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7da2e-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="7da2e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7da2e-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7da2e-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7da2e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7da2e-114">See also</span></span>

- [<span data-ttu-id="7da2e-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="7da2e-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="7da2e-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="7da2e-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
