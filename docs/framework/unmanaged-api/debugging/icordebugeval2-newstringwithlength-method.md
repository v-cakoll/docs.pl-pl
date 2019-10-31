---
title: ICorDebugEval2::NewStringWithLength — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugEval2.NewStringWithLength
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugEval2::NewStringWithLength
helpviewer_keywords:
- NewStringWithLength method [.NET Framework debugging]
- ICorDebugEval2::NewStringWithLength method [.NET Framework debugging]
ms.assetid: d5f54a34-6335-4708-b407-a756ec70fab4
topic_type:
- apiref
ms.openlocfilehash: 3836b6c08098d38516c8a25260fb28998a2317fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73084785"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="28c57-102">ICorDebugEval2::NewStringWithLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="28c57-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="28c57-103">Tworzy ciąg o określonej długości z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="28c57-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="28c57-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="28c57-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="28c57-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="28c57-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="28c57-106">podczas Wskaźnik do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="28c57-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="28c57-107">podczas Długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="28c57-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="28c57-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="28c57-108">Remarks</span></span>  
 <span data-ttu-id="28c57-109">Jeśli oczekiwany znak null ciągu powinien znajdować się w ciągu zarządzanym, wywołujący metodę `NewStringWithLength` musi mieć pewność, że długość ciągu zawiera końcowy znak null.</span><span class="sxs-lookup"><span data-stu-id="28c57-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="28c57-110">Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="28c57-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="28c57-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="28c57-111">Requirements</span></span>  
 <span data-ttu-id="28c57-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="28c57-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="28c57-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="28c57-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="28c57-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="28c57-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="28c57-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="28c57-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
