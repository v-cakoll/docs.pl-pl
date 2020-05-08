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
ms.openlocfilehash: a2b76cb59a95082e0cf9c0884b8277cca3c8fe8d
ms.sourcegitcommit: fff146ba3fd1762c8c432d95c8b877825ae536fc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/08/2020
ms.locfileid: "82976073"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="4a86d-102">ICorDebugEval2::NewStringWithLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="4a86d-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="4a86d-103">Tworzy ciąg o określonej długości z określoną zawartością.</span><span class="sxs-lookup"><span data-stu-id="4a86d-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4a86d-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4a86d-104">Syntax</span></span>  
  
```cpp  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4a86d-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="4a86d-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="4a86d-106">podczas Wskaźnik do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="4a86d-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="4a86d-107">podczas Długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="4a86d-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4a86d-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4a86d-108">Remarks</span></span>  
 <span data-ttu-id="4a86d-109">Jeśli oczekiwany znak null ciągu powinien znajdować się w zarządzanym ciągu, obiekt wywołujący `NewStringWithLength` metody musi mieć pewność, że długość ciągu zawiera końcowy znak null.</span><span class="sxs-lookup"><span data-stu-id="4a86d-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="4a86d-110">Ten ciąg jest zawsze tworzony w domenie aplikacji, w której jest aktualnie wykonywany wątek.</span><span class="sxs-lookup"><span data-stu-id="4a86d-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4a86d-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4a86d-111">Requirements</span></span>  
 <span data-ttu-id="4a86d-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4a86d-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4a86d-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="4a86d-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="4a86d-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="4a86d-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4a86d-115">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4a86d-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
