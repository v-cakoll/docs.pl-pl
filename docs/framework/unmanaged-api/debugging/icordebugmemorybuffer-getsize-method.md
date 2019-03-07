---
title: Metoda ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6fdf5e6e52b0c650e56368493074ea7db8e5bac9
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485437"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="8a679-102">Metoda ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="8a679-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="8a679-103">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="8a679-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8a679-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8a679-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8a679-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8a679-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="8a679-106">[out] Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="8a679-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8a679-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8a679-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a679-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="8a679-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8a679-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8a679-109">Requirements</span></span>  
 <span data-ttu-id="8a679-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8a679-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8a679-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8a679-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8a679-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8a679-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8a679-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8a679-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8a679-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a679-114">See also</span></span>
- [<span data-ttu-id="8a679-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="8a679-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="8a679-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="8a679-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
