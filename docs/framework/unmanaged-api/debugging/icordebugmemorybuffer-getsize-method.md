---
title: Metoda ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d687f2bbd3c20564368d4246961b56382ea14cf5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61916555"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="0c6b5-102">Metoda ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="0c6b5-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="0c6b5-103">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="0c6b5-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c6b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c6b5-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0c6b5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c6b5-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="0c6b5-106">[out] Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="0c6b5-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c6b5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c6b5-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0c6b5-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="0c6b5-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c6b5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c6b5-109">Requirements</span></span>  
 <span data-ttu-id="0c6b5-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c6b5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c6b5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c6b5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c6b5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c6b5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c6b5-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c6b5-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0c6b5-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0c6b5-114">See also</span></span>

- [<span data-ttu-id="0c6b5-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="0c6b5-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="0c6b5-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="0c6b5-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
