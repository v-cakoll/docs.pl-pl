---
title: Metoda ICorDebugMemoryBuffer::GetSize
ms.date: 03/30/2017
ms.assetid: 9ffd5482-268e-4680-9fd1-bfb0b7d66450
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c5984addb41c33468068f7ad24a15533f75dc367
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54714727"
---
# <a name="icordebugmemorybuffergetsize-method"></a><span data-ttu-id="cd698-102">Metoda ICorDebugMemoryBuffer::GetSize</span><span class="sxs-lookup"><span data-stu-id="cd698-102">ICorDebugMemoryBuffer::GetSize Method</span></span>
<span data-ttu-id="cd698-103">Pobiera rozmiar bufora pamięci w bajtach.</span><span class="sxs-lookup"><span data-stu-id="cd698-103">Gets the size of the memory buffer in bytes.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd698-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd698-104">Syntax</span></span>  
  
```  
HRESULT GetSize(  
   [out] ULONG32 *pcbBufferLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="cd698-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="cd698-105">Parameters</span></span>  
 `pcbBufferLength`  
 <span data-ttu-id="cd698-106">[out] Wskaźnik do rozmiaru bufora pamięci.</span><span class="sxs-lookup"><span data-stu-id="cd698-106">[out] A pointer to the size of the memory buffer.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="cd698-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="cd698-107">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cd698-108">Ta metoda jest tylko dostępne z architekturą .NET Native.</span><span class="sxs-lookup"><span data-stu-id="cd698-108">This method is available with .NET Native only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cd698-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd698-109">Requirements</span></span>  
 <span data-ttu-id="cd698-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd698-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd698-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cd698-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cd698-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cd698-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cd698-113">**Wersje programu .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd698-113">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd698-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd698-114">See also</span></span>
- [<span data-ttu-id="cd698-115">ICorDebugMemoryBuffer, interfejs</span><span class="sxs-lookup"><span data-stu-id="cd698-115">ICorDebugMemoryBuffer Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmemorybuffer-interface.md)
- [<span data-ttu-id="cd698-116">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="cd698-116">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
