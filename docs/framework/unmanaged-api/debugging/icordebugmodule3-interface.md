---
title: ICorDebugModule3 — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugModule3
api_location:
- CorDebug.dll
api_type:
- COM
f1_keywords:
- ICorDebugModule3
helpviewer_keywords:
- ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type:
- apiref
ms.openlocfilehash: 07919398b658d735fe4c9818ab24d27d586b6629
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122560"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="92706-102">ICorDebugModule3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="92706-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="92706-103">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="92706-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92706-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="92706-104">Syntax</span></span>  
  
```cpp  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="92706-105">Metody</span><span class="sxs-lookup"><span data-stu-id="92706-105">Methods</span></span>  
  
|<span data-ttu-id="92706-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="92706-106">Method</span></span>|<span data-ttu-id="92706-107">Opis</span><span class="sxs-lookup"><span data-stu-id="92706-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="92706-108">ICorDebugModule3::CreateReaderForInMemorySymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="92706-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="92706-109">Tworzy czytnik symboli (zazwyczaj [interfejs ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="92706-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92706-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="92706-110">Remarks</span></span>  
 <span data-ttu-id="92706-111">Ten interfejs logicznie rozszerza interfejsy "ICorDebugModule" i "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="92706-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="92706-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="92706-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92706-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="92706-113">Requirements</span></span>  
 <span data-ttu-id="92706-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92706-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92706-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="92706-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92706-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="92706-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92706-117">**.NET Framework wersje:** 4,5, 4, 3,5 SP1</span><span class="sxs-lookup"><span data-stu-id="92706-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="92706-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92706-118">See also</span></span>

- [<span data-ttu-id="92706-119">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="92706-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="92706-120">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="92706-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="92706-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="92706-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
