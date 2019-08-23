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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e51ff64115ce3417087eee6845aa802ad64f2a72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69961004"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="a0aea-102">ICorDebugModule3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="a0aea-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="a0aea-103">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="a0aea-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0aea-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a0aea-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="a0aea-105">Metody</span><span class="sxs-lookup"><span data-stu-id="a0aea-105">Methods</span></span>  
  
|<span data-ttu-id="a0aea-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="a0aea-106">Method</span></span>|<span data-ttu-id="a0aea-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a0aea-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a0aea-108">ICorDebugModule3::CreateReaderForInMemorySymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="a0aea-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="a0aea-109">Tworzy czytnik symboli (zazwyczaj [interfejs ISymUnmanagedReader](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="a0aea-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a0aea-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0aea-110">Remarks</span></span>  
 <span data-ttu-id="a0aea-111">Ten interfejs logicznie rozszerza interfejsy "ICorDebugModule" i "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="a0aea-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a0aea-112">Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.</span><span class="sxs-lookup"><span data-stu-id="a0aea-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a0aea-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a0aea-113">Requirements</span></span>  
 <span data-ttu-id="a0aea-114">**Poszczególnych** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0aea-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0aea-115">**Nagłówki** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a0aea-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a0aea-116">**Biblioteki** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0aea-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0aea-117">**.NET Framework wersje:** 4,5, 4, 3,5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="a0aea-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a0aea-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0aea-118">See also</span></span>

- [<span data-ttu-id="a0aea-119">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0aea-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="a0aea-120">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="a0aea-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="a0aea-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="a0aea-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
