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
ms.openlocfilehash: 1d504e694810bfa1b9f3258f75e307bfb60d4ad7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496809"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="ba0bb-102">ICorDebugModule3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="ba0bb-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="ba0bb-103">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ba0bb-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ba0bb-104">Syntax</span></span>  
  
```  
interface ICorDebugModule3 : IUnknown  
{  
    HRESULT CreateReaderForInMemorySymbols  
      (  
      [in] REFIID riid,  
      [out][iid_is(riid)] void **  ppObj  
      );  
};  
```  
  
## <a name="methods"></a><span data-ttu-id="ba0bb-105">Metody</span><span class="sxs-lookup"><span data-stu-id="ba0bb-105">Methods</span></span>  
  
|<span data-ttu-id="ba0bb-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="ba0bb-106">Method</span></span>|<span data-ttu-id="ba0bb-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ba0bb-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ba0bb-108">ICorDebugModule3::CreateReaderForInMemorySymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="ba0bb-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="ba0bb-109">Tworzy czytnik symbolu (zazwyczaj [isymunmanagedreader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ba0bb-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ba0bb-110">Remarks</span></span>  
 <span data-ttu-id="ba0bb-111">Ten interfejs rozszerza logicznie interfejsów "ICorDebugModule" i "Icordebugmodule2 —".</span><span class="sxs-lookup"><span data-stu-id="ba0bb-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ba0bb-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="ba0bb-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ba0bb-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ba0bb-113">Requirements</span></span>  
 <span data-ttu-id="ba0bb-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ba0bb-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ba0bb-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ba0bb-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ba0bb-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ba0bb-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ba0bb-117">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="ba0bb-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ba0bb-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba0bb-118">See also</span></span>
- [<span data-ttu-id="ba0bb-119">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba0bb-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="ba0bb-120">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="ba0bb-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="ba0bb-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="ba0bb-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
