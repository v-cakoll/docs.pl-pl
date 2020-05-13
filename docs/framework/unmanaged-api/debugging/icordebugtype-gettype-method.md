---
title: ICorDebugType::GetType — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
ms.openlocfilehash: ac42c6254182ea775377a448a54d527b234c97dc
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379924"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="956ab-102">ICorDebugType::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="956ab-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="956ab-103">Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> reprezentowanego przez ten ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="956ab-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="956ab-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="956ab-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="956ab-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="956ab-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="956ab-106">określoną Wskaźnik do wartości `CorElementType` wyliczenia wskazującej, że środowisko CLR <xref:System.Type> `ICorDebugType` reprezentuje.</span><span class="sxs-lookup"><span data-stu-id="956ab-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="956ab-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="956ab-107">Remarks</span></span>  
 <span data-ttu-id="956ab-108">Jeśli wartość `ty` jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, Metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) może zostać wywołana w celu pobrania niewystąpienia typu dla typu ogólnego; w przeciwnym razie nie należy wywoływać `ICorDebugType::GetClass` .</span><span class="sxs-lookup"><span data-stu-id="956ab-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="956ab-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="956ab-109">Requirements</span></span>  
 <span data-ttu-id="956ab-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="956ab-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="956ab-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="956ab-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="956ab-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="956ab-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="956ab-113">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="956ab-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
