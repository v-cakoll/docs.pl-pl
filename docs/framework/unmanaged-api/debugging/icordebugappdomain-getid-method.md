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
ms.openlocfilehash: 8122f1b5017faac3425d59d12d77f84180134d65
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="a52a8-102">ICorDebugAppDomain::GetId — Metoda</span><span class="sxs-lookup"><span data-stu-id="a52a8-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="a52a8-103">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a52a8-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a52a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a52a8-104">Syntax</span></span>  
  
```  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a52a8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a52a8-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="a52a8-106">[out] Unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a52a8-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a52a8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a52a8-107">Remarks</span></span>  
 <span data-ttu-id="a52a8-108">Identyfikator domeny aplikacji jest unikatowa w ramach procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="a52a8-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a52a8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a52a8-109">Requirements</span></span>  
 <span data-ttu-id="a52a8-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a52a8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a52a8-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a52a8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a52a8-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a52a8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a52a8-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a52a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
