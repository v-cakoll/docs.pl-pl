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
ms.openlocfilehash: 972a981188c36236b81f3da17c09abeeb1e32857
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212194"
---
# <a name="icordebuggenericvaluesetvalue-method"></a><span data-ttu-id="f9a55-102">ICorDebugGenericValue::SetValue — Metoda</span><span class="sxs-lookup"><span data-stu-id="f9a55-102">ICorDebugGenericValue::SetValue Method</span></span>
<span data-ttu-id="f9a55-103">Kopiuje nową wartość z określonego buforu.</span><span class="sxs-lookup"><span data-stu-id="f9a55-103">Copies a new value from the specified buffer.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9a55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f9a55-104">Syntax</span></span>  
  
```cpp  
HRESULT SetValue (  
    [in] void      *pFrom  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f9a55-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="f9a55-105">Parameters</span></span>  
 `pFrom`  
 <span data-ttu-id="f9a55-106">podczas Wskaźnik do buforu, z którego ma zostać skopiowana wartość.</span><span class="sxs-lookup"><span data-stu-id="f9a55-106">[in] A pointer to the buffer from which to copy the value.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="f9a55-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9a55-107">Remarks</span></span>  
 <span data-ttu-id="f9a55-108">W przypadku typów referencyjnych wartością jest odwołanie, a nie zawartość.</span><span class="sxs-lookup"><span data-stu-id="f9a55-108">For reference types, the value is the reference, not the content.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9a55-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f9a55-109">Requirements</span></span>  
 <span data-ttu-id="f9a55-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9a55-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9a55-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="f9a55-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9a55-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="f9a55-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9a55-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9a55-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
