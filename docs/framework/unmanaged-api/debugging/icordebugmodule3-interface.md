---
title: "ICorDebugModule3 — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugModule3
api_location: CorDebug.dll
api_type: COM
f1_keywords: ICorDebugModule3
helpviewer_keywords: ICorDebugModule3 interface [.NET Framework debugging]
ms.assetid: 0b69f945-263a-4e11-8512-89d27f6ea296
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f6ef8314329aba60d8c23c6f00725192d83961ec
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugmodule3-interface"></a><span data-ttu-id="58d5d-102">ICorDebugModule3 — Interfejs</span><span class="sxs-lookup"><span data-stu-id="58d5d-102">ICorDebugModule3 Interface</span></span>
<span data-ttu-id="58d5d-103">Tworzy czytnik symbolu dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="58d5d-103">Creates a symbol reader for a dynamic module.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58d5d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="58d5d-104">Syntax</span></span>  
  
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
  
## <a name="methods"></a><span data-ttu-id="58d5d-105">Metody</span><span class="sxs-lookup"><span data-stu-id="58d5d-105">Methods</span></span>  
  
|<span data-ttu-id="58d5d-106">Metoda</span><span class="sxs-lookup"><span data-stu-id="58d5d-106">Method</span></span>|<span data-ttu-id="58d5d-107">Opis</span><span class="sxs-lookup"><span data-stu-id="58d5d-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="58d5d-108">ICorDebugModule3::CreateReaderForInMemorySymbols — metoda</span><span class="sxs-lookup"><span data-stu-id="58d5d-108">ICorDebugModule3::CreateReaderForInMemorySymbols Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugmodule3-createreaderforinmemorysymbols-method.md)|<span data-ttu-id="58d5d-109">Tworzy czytnika symboli (zazwyczaj [ISymUnmanagedReader — interfejs](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) dla modułu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="58d5d-109">Creates a symbol reader (typically [ISymUnmanagedReader Interface](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)) for a dynamic module.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="58d5d-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58d5d-110">Remarks</span></span>  
 <span data-ttu-id="58d5d-111">Ten interfejs rozszerza logicznie interfejsów "ICorDebugModule" i "ICorDebugModule2".</span><span class="sxs-lookup"><span data-stu-id="58d5d-111">This interface logically extends the "ICorDebugModule" and "ICorDebugModule2" interfaces.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58d5d-112">Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.</span><span class="sxs-lookup"><span data-stu-id="58d5d-112">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="58d5d-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="58d5d-113">Requirements</span></span>  
 <span data-ttu-id="58d5d-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="58d5d-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="58d5d-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="58d5d-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="58d5d-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="58d5d-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="58d5d-117">**Wersje programu .NET framework:**4.5, 4, 3.5 z dodatkiem SP1</span><span class="sxs-lookup"><span data-stu-id="58d5d-117">**.NET Framework Versions:**4.5, 4, 3.5 SP1</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58d5d-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58d5d-118">See Also</span></span>  
 [<span data-ttu-id="58d5d-119">ICorDebugRemoteTarget — interfejs</span><span class="sxs-lookup"><span data-stu-id="58d5d-119">ICorDebugRemoteTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugremotetarget-interface.md)  
 [<span data-ttu-id="58d5d-120">ICorDebug — interfejs</span><span class="sxs-lookup"><span data-stu-id="58d5d-120">ICorDebug Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebug-interface.md)  
    
 [<span data-ttu-id="58d5d-121">Interfejsy debugowania</span><span class="sxs-lookup"><span data-stu-id="58d5d-121">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
