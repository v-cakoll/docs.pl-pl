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
ms.openlocfilehash: b84a2fad53feda2996515781035c0eaad5828d54
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61666995"
---
# <a name="icordebugeval2newstringwithlength-method"></a><span data-ttu-id="78329-102">ICorDebugEval2::NewStringWithLength — Metoda</span><span class="sxs-lookup"><span data-stu-id="78329-102">ICorDebugEval2::NewStringWithLength Method</span></span>
<span data-ttu-id="78329-103">Tworzy ciąg o określonej długości, przy użyciu określonej zawartości.</span><span class="sxs-lookup"><span data-stu-id="78329-103">Creates a string of the specified length, with the specified contents.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78329-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="78329-104">Syntax</span></span>  
  
```  
HRESULT NewStringWithLength (  
    [in] LPCWSTR               string,  
    [in] UINT                  uiLength  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="78329-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="78329-105">Parameters</span></span>  
 `string`  
 <span data-ttu-id="78329-106">[in] Wskaźnik do wartości ciągu.</span><span class="sxs-lookup"><span data-stu-id="78329-106">[in] A pointer to the string value.</span></span>  
  
 `uiLength`  
 <span data-ttu-id="78329-107">[in] Długość ciągu.</span><span class="sxs-lookup"><span data-stu-id="78329-107">[in] Length of the string.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78329-108">Uwagi</span><span class="sxs-lookup"><span data-stu-id="78329-108">Remarks</span></span>  
 <span data-ttu-id="78329-109">Jeśli ciąg na końcu znak null powinien być w ciągu zarządzany obiekt wywołujący `NewStringWithLength` metody należy upewnić się, że długość ciągu zawiera końcowego znaku null.</span><span class="sxs-lookup"><span data-stu-id="78329-109">If the string's trailing null character is expected to be in the managed string, the caller of the `NewStringWithLength` method must ensure that the string length includes the trailing null character.</span></span>  
  
 <span data-ttu-id="78329-110">Ciąg zawsze jest tworzony w domenie aplikacji, w którym wątek jest w trakcie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="78329-110">The string is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78329-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="78329-111">Requirements</span></span>  
 <span data-ttu-id="78329-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78329-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78329-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78329-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78329-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78329-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78329-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="78329-115">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
