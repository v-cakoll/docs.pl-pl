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
ms.openlocfilehash: a340086be042c790ae7bf750759ff80f7c9eaf23
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61942444"
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="3222d-102">ICorDebugModule3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3222d-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="3222d-103">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="3222d-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3222d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3222d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="3222d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="3222d-105">Methods</span></span>  
  
|<span data-ttu-id="3222d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="3222d-106">Method</span></span>|<span data-ttu-id="3222d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3222d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="3222d-108">ICorDebugModule3::CreateReaderForInMemorySymbols, metoda</span><span class="sxs-lookup"><span data-stu-id="3222d-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="3222d-109">Tworzy czytnik symbolu (zazwyczaj [isymunmanagedreader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="3222d-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3222d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3222d-110">Remarks</span></span>  
 <span data-ttu-id="3222d-111">Ten interfejs rozszerza logicznie interfejsów "ICorDebugModule" i "Icordebugmodule2 —".</span><span class="sxs-lookup"><span data-stu-id="3222d-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3222d-112">Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.</span><span class="sxs-lookup"><span data-stu-id="3222d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3222d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3222d-113">Requirements</span></span>  
 <span data-ttu-id="3222d-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3222d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3222d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3222d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3222d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3222d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3222d-117">**Wersje programu .NET framework:** 4.5, 4, 3.5 Z DODATKIEM SP1</span><span class="sxs-lookup"><span data-stu-id="3222d-117">**.NET Framework Versions:** 4.5, 4, 3.5 SP1</span></span>
  
## <a name="see-also"></a><span data-ttu-id="3222d-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3222d-118">See also</span></span>

- [<span data-ttu-id="3222d-119">ICorDebugRemoteTarget, interfejs</span><span class="sxs-lookup"><span data-stu-id="3222d-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)
- [<span data-ttu-id="3222d-120">ICorDebug, interfejs</span><span class="sxs-lookup"><span data-stu-id="3222d-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)

- [<span data-ttu-id="3222d-121">Debugowanie, interfejsy</span><span class="sxs-lookup"><span data-stu-id="3222d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
