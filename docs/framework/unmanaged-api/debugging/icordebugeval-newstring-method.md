---
title: ICorDebugEval::NewString — Metoda
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: db609bdee7975b6c067271f99529e2cf2240f720
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57480185"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="c3e8c-102">ICorDebugEval::NewString — Metoda</span><span class="sxs-lookup"><span data-stu-id="c3e8c-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="c3e8c-103">Przydziela nowego wystąpienia ciągu przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="c3e8c-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c3e8c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="c3e8c-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c3e8c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="c3e8c-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="c3e8c-106">[in] Wskaźnik do zawartości dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="c3e8c-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c3e8c-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c3e8c-107">Remarks</span></span>  
 <span data-ttu-id="c3e8c-108">Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="c3e8c-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c3e8c-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="c3e8c-109">Requirements</span></span>  
 <span data-ttu-id="c3e8c-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c3e8c-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c3e8c-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c3e8c-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c3e8c-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c3e8c-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c3e8c-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c3e8c-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
