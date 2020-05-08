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
ms.openlocfilehash: b263fed7db5cb2ef687da45f8cbc99a02e1e3ea2
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976138"
---
# <a name="icordebugevalnewstring-method"></a><span data-ttu-id="8d081-102">ICorDebugEval::NewString — Metoda</span><span class="sxs-lookup"><span data-stu-id="8d081-102">ICorDebugEval::NewString Method</span></span>
<span data-ttu-id="8d081-103">Przydziela nowe wystąpienie ciągu z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="8d081-103">Allocates a new string instance with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8d081-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8d081-104">Syntax</span></span>  
  
```cpp  
HRESULT NewString (  
    [in] LPCWSTR   string  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="8d081-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="8d081-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="8d081-106">podczas Wskaźnik do zawartości dla ciągu.</span><span class="sxs-lookup"><span data-stu-id="8d081-106">[in] Pointer to the contents for the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="8d081-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="8d081-107">Remarks</span></span>  
 <span data-ttu-id="8d081-108">Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="8d081-108">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8d081-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8d081-109">Requirements</span></span>  
 <span data-ttu-id="8d081-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8d081-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8d081-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="8d081-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8d081-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="8d081-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8d081-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8d081-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
