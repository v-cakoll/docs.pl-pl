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
ms.openlocfilehash: e5eb86bb80aea5fc65a7362467b78b16a59794d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33412233"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="a6808-102">ICorDebugEval::NewString — Metoda</span><span class="sxs-lookup"><span data-stu-id="a6808-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="a6808-103">Przydziela nowego wystąpienia ciągu przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="a6808-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6808-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a6808-104">Syntax</span></span>  
  
```  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a6808-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="a6808-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="a6808-106">[in] Wskaźnik do zawartości dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="a6808-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a6808-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a6808-107">Remarks</span></span>  
 <span data-ttu-id="a6808-108">Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="a6808-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6808-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a6808-109">Requirements</span></span>  
 <span data-ttu-id="a6808-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6808-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6808-111">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a6808-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a6808-112">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6808-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6808-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6808-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
