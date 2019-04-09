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
ms.openlocfilehash: 021068caa8f1ad2c64e5ca3d18ea25dc827563a4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085007"
---
# <a name="icorpublishgetprocess-method"></a><span data-ttu-id="f598e-102">ICorPublish::GetProcess — Metoda</span><span class="sxs-lookup"><span data-stu-id="f598e-102">ICorPublish::GetProcess Method</span></span>
<span data-ttu-id="f598e-103">Pobiera [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) wystąpienia, który reprezentuje proces o określonym identyfikatorze.</span><span class="sxs-lookup"><span data-stu-id="f598e-103">Gets an [ICorPublishProcess](../../../../docs/framework/unmanaged-api/debugging/icorpublishprocess-interface.md) instance that represents the process with the specified identifier.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f598e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f598e-104">Syntax</span></span>  
  
```  
HRESULT GetProcess(  
    [in] unsigned              pid,   
    [out] ICorPublishProcess   **ppProcess  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f598e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f598e-105">Parameters</span></span>  
 `pid`  
 <span data-ttu-id="f598e-106">[in] Identyfikator procesu.</span><span class="sxs-lookup"><span data-stu-id="f598e-106">[in] The identifier of the process.</span></span>  
  
 `ppProcess`  
 <span data-ttu-id="f598e-107">[out] Wskaźnik na adres `ICorPublishProcess` wystąpienia, który reprezentuje proces.</span><span class="sxs-lookup"><span data-stu-id="f598e-107">[out] A pointer to the address of an `ICorPublishProcess` instance that represents the process.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f598e-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f598e-108">Remarks</span></span>  
 `GetProcess` <span data-ttu-id="f598e-109">kończy się niepowodzeniem, jeśli proces nie istnieje lub nie jest zarządzany proces, który może być debugowany przez bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f598e-109">fails if the process doesn't exist, or isn't a managed process that can be debugged by the current user.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f598e-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f598e-110">Requirements</span></span>  
 <span data-ttu-id="f598e-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f598e-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f598e-112">**Nagłówek:** CorPub.idl, CorPub.h</span><span class="sxs-lookup"><span data-stu-id="f598e-112">**Header:** CorPub.idl, CorPub.h</span></span>  
  
 <span data-ttu-id="f598e-113">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f598e-113">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="f598e-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="f598e-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="f598e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f598e-115">See also</span></span>

- [<span data-ttu-id="f598e-116">ICorPublish — Interfejs</span><span class="sxs-lookup"><span data-stu-id="f598e-116">ICorPublish Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icorpublish-interface.md)
