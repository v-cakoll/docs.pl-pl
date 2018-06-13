---
title: ICorDebugVariableHome::GetLocationType — metoda
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
ms.openlocfilehash: c04fa944f2a3da9b6548ada36443d5dda4725f21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421132"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="512f8-102">ICorDebugVariableHome::GetLocationType — metoda</span><span class="sxs-lookup"><span data-stu-id="512f8-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="512f8-103">Pobiera typ zmiennej natywnego lokalizacji.</span><span class="sxs-lookup"><span data-stu-id="512f8-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="512f8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="512f8-104">Syntax</span></span>  
  
```  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="512f8-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="512f8-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="512f8-106">[out] Wskaźnik do typu natywnego lokalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="512f8-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="512f8-107">Zobacz [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) wyliczenia, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="512f8-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="512f8-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="512f8-108">Requirements</span></span>  
 <span data-ttu-id="512f8-109">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="512f8-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="512f8-110">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="512f8-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="512f8-111">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="512f8-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="512f8-112">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="512f8-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="512f8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="512f8-113">See Also</span></span>  
 [<span data-ttu-id="512f8-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="512f8-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)  
 [<span data-ttu-id="512f8-115">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="512f8-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
