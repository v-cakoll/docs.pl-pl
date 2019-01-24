---
title: ICorDebugVariableHome::GetLocationType Method
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetLocationType
helpviewer_keywords:
- ICorDebugVariableHome::GetLocationType method [.NET Framework debugging]
- GetLocationType method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 88027c55-8ec6-4f1e-a55b-7eefdbbc3515
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3080196076aefbee6bb484063994abe54eb3f53b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716998"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="33059-102">ICorDebugVariableHome::GetLocationType Method</span><span class="sxs-lookup"><span data-stu-id="33059-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="33059-103">Pobiera typ zmiennej natywnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="33059-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="33059-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="33059-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="33059-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="33059-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="33059-106">[out] Wskaźnik do typu zmiennej natywnych lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="33059-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="33059-107">Zobacz [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) wyliczenie, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="33059-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="33059-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="33059-108">Requirements</span></span>  
 <span data-ttu-id="33059-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="33059-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="33059-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="33059-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="33059-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="33059-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="33059-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="33059-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33059-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="33059-113">See also</span></span>
- [<span data-ttu-id="33059-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="33059-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="33059-115">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="33059-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
