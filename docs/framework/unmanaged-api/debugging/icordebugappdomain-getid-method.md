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
ms.openlocfilehash: 63346c679efc083dea9ab0eaa4f983a5308695f8
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895251"
---
# <a name="icordebugappdomaingetid-method"></a><span data-ttu-id="b1385-102">ICorDebugAppDomain::GetId — Metoda</span><span class="sxs-lookup"><span data-stu-id="b1385-102">ICorDebugAppDomain::GetId Method</span></span>
<span data-ttu-id="b1385-103">Pobiera unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1385-103">Gets the unique identifier of the application domain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b1385-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b1385-104">Syntax</span></span>  
  
```cpp  
HRESULT GetID (  
    [out] ULONG32   *pId  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b1385-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b1385-105">Parameters</span></span>  
 `pId`  
 <span data-ttu-id="b1385-106">określoną Unikatowy identyfikator domeny aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b1385-106">[out] The unique identifier of the application domain.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b1385-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b1385-107">Remarks</span></span>  
 <span data-ttu-id="b1385-108">Identyfikator domeny aplikacji jest unikatowy w ramach procesu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="b1385-108">The identifier for the application domain is unique within the containing process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b1385-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b1385-109">Requirements</span></span>  
 <span data-ttu-id="b1385-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b1385-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b1385-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="b1385-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b1385-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="b1385-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b1385-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b1385-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
