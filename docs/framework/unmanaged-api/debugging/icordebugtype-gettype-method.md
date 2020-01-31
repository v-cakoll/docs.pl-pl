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
ms.openlocfilehash: 25ffbf73fbefbb3c584450283c3080dfc11ee598
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791241"
---
# <a name="icordebugtypegettype-method"></a><span data-ttu-id="d0099-102">ICorDebugType::GetType — Metoda</span><span class="sxs-lookup"><span data-stu-id="d0099-102">ICorDebugType::GetType Method</span></span>
<span data-ttu-id="d0099-103">Pobiera wartość CorElementType —, która opisuje typ natywny środowiska uruchomieniowego języka wspólnego (CLR) <xref:System.Type> reprezentowane przez ten ICorDebugType.</span><span class="sxs-lookup"><span data-stu-id="d0099-103">Gets a CorElementType value that describes the native type of the common language runtime (CLR) <xref:System.Type> represented by this ICorDebugType.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d0099-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d0099-104">Syntax</span></span>  
  
```cpp  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d0099-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="d0099-105">Parameters</span></span>  
 `ty`  
 <span data-ttu-id="d0099-106">określoną Wskaźnik do wartości wyliczenia `CorElementType`, który wskazuje <xref:System.Type> CLR, który reprezentuje `ICorDebugType`.</span><span class="sxs-lookup"><span data-stu-id="d0099-106">[out] A pointer to a value of the `CorElementType` enumeration that indicates the CLR <xref:System.Type> that this `ICorDebugType` represents.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d0099-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d0099-107">Remarks</span></span>  
 <span data-ttu-id="d0099-108">Jeśli wartość `ty` jest ELEMENT_TYPE_CLASS lub ELEMENT_TYPE_VALUETYPE, Metoda [ICorDebugType:: GetClass](icordebugtype-getclass-method.md) może zostać wywołana w celu pobrania typu niewystąpienia dla typu ogólnego; w przeciwnym razie nie wywołuj `ICorDebugType::GetClass`.</span><span class="sxs-lookup"><span data-stu-id="d0099-108">If the value of `ty` is either ELEMENT_TYPE_CLASS or ELEMENT_TYPE_VALUETYPE, the [ICorDebugType::GetClass](icordebugtype-getclass-method.md) method may be called to get the uninstantiated type for a generic type; otherwise, do not call `ICorDebugType::GetClass`.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d0099-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d0099-109">Requirements</span></span>  
 <span data-ttu-id="d0099-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d0099-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d0099-111">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="d0099-111">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d0099-112">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="d0099-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d0099-113">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d0099-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
