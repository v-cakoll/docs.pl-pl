---
title: ICorPublish::GetProcess — Metoda
ms.date: 03/30/2017
api_name:
- ICorPublish.GetProcess
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorPublish::GetProcess
helpviewer_keywords:
- ICorPublish::GetProcess method [.NET Framework debugging]
- GetProcess method, ICorPublish interface [.NET Framework debugging]
ms.assetid: c5143805-2eb7-45b8-85ed-c8fb34df1084
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414bc1bbd3578d0707e35fa70fe196b504af9942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418499"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="334fc-102">ICorPublish::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="334fc-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="334fc-103">Pobiera [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wystąpienia, który reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="334fc-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="334fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="334fc-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="334fc-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="334fc-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="334fc-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="334fc-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="334fc-107">[out] Wskaźnik do adresu `ICorPublishProcess` wystąpienia, który reprezentuje procesu.</span><span class="sxs-lookup"><span data-stu-id="334fc-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="334fc-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="334fc-108">Remarks</span></span>  
 <span data-ttu-id="334fc-109">`GetProcess` kończy się niepowodzeniem, jeśli proces nie istnieje lub nie jest zarządzany proces, który może być debugowany przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="334fc-109">`GetProcess` fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="334fc-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="334fc-110">Requirements</span></span>  
 <span data-ttu-id="334fc-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="334fc-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="334fc-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="334fc-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="334fc-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="334fc-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="334fc-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="334fc-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="334fc-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="334fc-115">See Also</span></span>  
 [<span data-ttu-id="334fc-116">ICorPublish, interfejs</span><span class="sxs-lookup"><span data-stu-id="334fc-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
