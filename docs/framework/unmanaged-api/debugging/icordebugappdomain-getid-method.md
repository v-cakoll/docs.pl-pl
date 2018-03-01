---
title: "ICorDebugAppDomain::GetId — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8b151d5b0774576e98da5845e5c7afc24ada0001
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="088a5-102">ICorDebugAppDomain::GetId — Metoda</span><span class="sxs-lookup"><span data-stu-id="088a5-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="088a5-103">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="088a5-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="088a5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="088a5-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="088a5-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="088a5-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="088a5-106">[out] Unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="088a5-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="088a5-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="088a5-107">Remarks</span></span>  
 <span data-ttu-id="088a5-108">Identyfikator domeny aplikacji jest unikatowa w ramach procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="088a5-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="088a5-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="088a5-109">Requirements</span></span>  
 <span data-ttu-id="088a5-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="088a5-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="088a5-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="088a5-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="088a5-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="088a5-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="088a5-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="088a5-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
