---
title: ICorDebugMemoryBuffer::GetSize — metoda
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: caf95e0b5c8d4ae942bb428f53d4e58313e0e78e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33414755"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="2d32f-102">ICorDebugMemoryBuffer::GetSize — metoda</span><span class="sxs-lookup"><span data-stu-id="2d32f-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="2d32f-103">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="2d32f-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d32f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d32f-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="2d32f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="2d32f-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="2d32f-106">[out] Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="2d32f-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="2d32f-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d32f-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2d32f-108">Ta metoda jest tylko dostępne z platformą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="2d32f-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d32f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d32f-109">Requirements</span></span>  
 <span data-ttu-id="2d32f-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d32f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d32f-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2d32f-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2d32f-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d32f-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d32f-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d32f-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d32f-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d32f-114">See Also</span></span>  
 [<span data-ttu-id="2d32f-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="2d32f-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)  
 [<span data-ttu-id="2d32f-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="2d32f-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
