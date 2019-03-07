---
title: ICorDebugAppDomain::GetId — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain.GetId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain::GetId
helpviewer_keywords:
- GetId method, ICorDebugAppDomain interface [.NET Framework debugging]
- ICorDebugAppDomain::GetId method [.NET Framework debugging]
ms.assetid: 32c27576-71fa-42ee-8230-67b92913ea08
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0aefc19ca0c255c9c8ea40fcc12fc5cba1b00f6
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57501457"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="ce60e-102">ICorDebugAppDomain::GetId — Metoda</span><span class="sxs-lookup"><span data-stu-id="ce60e-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="ce60e-103">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce60e-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ce60e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ce60e-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="ce60e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="ce60e-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="ce60e-106">[out] Unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="ce60e-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ce60e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce60e-107">Remarks</span></span>  
 <span data-ttu-id="ce60e-108">Identyfikator domeny aplikacji jest unikatowa w ramach procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="ce60e-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ce60e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ce60e-109">Requirements</span></span>  
 <span data-ttu-id="ce60e-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ce60e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ce60e-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="ce60e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="ce60e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="ce60e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="ce60e-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ce60e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
