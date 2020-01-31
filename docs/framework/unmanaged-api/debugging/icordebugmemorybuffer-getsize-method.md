---
title: 'ICorDebugMemoryBuffer:: GetSize — metoda'
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
ms.openlocfilehash: 51c13b67951c714d1aec602ffea22891328565a0
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793185"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="8a536-102">ICorDebugMemoryBuffer:: GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="8a536-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="8a536-103">Pobiera rozmiar buforu pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8a536-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a536-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a536-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a536-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a536-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="8a536-106">określoną Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="8a536-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a536-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a536-107">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8a536-108">Ta metoda jest dostępna tylko z .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8a536-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a536-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a536-109">Requirements</span></span>  
 <span data-ttu-id="8a536-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a536-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a536-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8a536-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a536-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8a536-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a536-113">**Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a536-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a536-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a536-114">See also</span></span>

- [<span data-ttu-id="8a536-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a536-115">ICorDebugMemoryBuffer Interface</span></span>](icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="8a536-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a536-116">Debugging Interfaces</span></span>](debugging-interfaces.md)
