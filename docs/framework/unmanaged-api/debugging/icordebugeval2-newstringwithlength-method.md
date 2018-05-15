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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6b3b77a0ffc7af3b3640d1b255bd3be522f45a7a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="0c29c-102">ICorDebugEval2::NewStringWithLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="0c29c-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="0c29c-103">Tworzy ciąg o określonej długości, przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="0c29c-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c29c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0c29c-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0c29c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0c29c-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="0c29c-106">[in] Wskaźnik do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="0c29c-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="0c29c-107">[in] Długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="0c29c-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0c29c-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0c29c-108">Remarks</span></span>  
 <span data-ttu-id="0c29c-109">Jeśli ciąg na końcu znak null powinien być w ciągu zarządzany element wywołujący `NewStringWithLength` metody musi zapewnić, że długość ciągu zawiera znak końcowy null.</span><span class="sxs-lookup"><span data-stu-id="0c29c-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="0c29c-110">Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest aktualnie wykonywany.</span><span class="sxs-lookup"><span data-stu-id="0c29c-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0c29c-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0c29c-111">Requirements</span></span>  
 <span data-ttu-id="0c29c-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0c29c-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0c29c-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0c29c-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0c29c-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0c29c-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0c29c-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0c29c-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
