---
title: "ICorDebugEval::NewString — Metoda"
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
- ICorDebugEval.NewString
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval::NewString
helpviewer_keywords:
- NewString method [.NET Framework debugging]
- ICorDebugEval::NewString method [.NET Framework debugging]
ms.assetid: 29e7a14b-d50e-4852-bfda-011b76c0c9ee
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6cc45d766801391fcd157c39357058be17759f8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="b994e-102">ICorDebugEval::NewString — Metoda</span><span class="sxs-lookup"><span data-stu-id="b994e-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="b994e-103">Przydziela nowego wystąpienia ciągu przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="b994e-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b994e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="b994e-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b994e-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="b994e-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="b994e-106">[in] Wskaźnik do zawartości dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="b994e-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="b994e-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="b994e-107">Remarks</span></span>  
 <span data-ttu-id="b994e-108">Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="b994e-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b994e-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="b994e-109">Requirements</span></span>  
 <span data-ttu-id="b994e-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b994e-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b994e-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b994e-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b994e-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b994e-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b994e-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b994e-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
