---
title: ICorDebugGenericValue::SetValue — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugGenericValue.SetValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGenericValue::SetValue
helpviewer_keywords:
- ICorDebugGenericValue::SetValue method [.NET Framework debugging]
- SetValue method, ICorDebugGenericValue interface [.NET Framework debugging]
ms.assetid: ed4c6458-0435-44fc-8e78-8ba00be362f2
topic_type:
- apiref
ms.openlocfilehash: 4cd03895b4e33c3e42c71acca12eaf950fc9a145
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138556"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="154d3-102">ICorDebugGenericValue::SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="154d3-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="154d3-103">Kopiuje nową wartość z określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="154d3-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="154d3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="154d3-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="154d3-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="154d3-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="154d3-106">podczas Wskaźnik do buforu, z którego ma zostać skopiowana wartość.</span><span class="sxs-lookup"><span data-stu-id="154d3-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="154d3-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="154d3-107">Remarks</span></span>  
 <span data-ttu-id="154d3-108">W przypadku typów referencyjnych wartością jest odwołanie, a nie zawartość.</span><span class="sxs-lookup"><span data-stu-id="154d3-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="154d3-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="154d3-109">Requirements</span></span>  
 <span data-ttu-id="154d3-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="154d3-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="154d3-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="154d3-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="154d3-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="154d3-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="154d3-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="154d3-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
