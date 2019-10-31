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
ms.openlocfilehash: 8a5d421bf0eb8ec5a34fe21d6efc79bbe56c294c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137645"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="122e8-102">ICorDebugEval::NewString — Metoda</span><span class="sxs-lookup"><span data-stu-id="122e8-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="122e8-103">Przydziela nowe wystąpienie ciągu z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="122e8-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="122e8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="122e8-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="122e8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="122e8-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="122e8-106">podczas Wskaźnik do zawartości dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="122e8-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="122e8-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="122e8-107">Remarks</span></span>  
 <span data-ttu-id="122e8-108">Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="122e8-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="122e8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="122e8-109">Requirements</span></span>  
 <span data-ttu-id="122e8-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="122e8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="122e8-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="122e8-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="122e8-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="122e8-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="122e8-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="122e8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
