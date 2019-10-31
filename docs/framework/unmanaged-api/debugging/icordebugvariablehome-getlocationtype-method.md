---
title: 'ICorDebugVariableHome:: getlocationtype — Metoda'
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
ms.openlocfilehash: 1dd4e9510831b4c878e9c1246dabe4add919130c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125113"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="51d59-102">ICorDebugVariableHome:: getlocationtype — Metoda</span><span class="sxs-lookup"><span data-stu-id="51d59-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="51d59-103">Pobiera typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="51d59-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="51d59-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="51d59-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="51d59-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="51d59-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="51d59-106">określoną Wskaźnik do typu lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="51d59-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="51d59-107">Aby uzyskać więcej informacji, zobacz Wyliczenie [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="51d59-107">See the [VariableLocationType](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="51d59-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="51d59-108">Requirements</span></span>  
 <span data-ttu-id="51d59-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="51d59-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="51d59-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="51d59-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="51d59-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="51d59-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="51d59-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="51d59-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="51d59-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51d59-113">See also</span></span>

- [<span data-ttu-id="51d59-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="51d59-114">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
- [<span data-ttu-id="51d59-115">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="51d59-115">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
