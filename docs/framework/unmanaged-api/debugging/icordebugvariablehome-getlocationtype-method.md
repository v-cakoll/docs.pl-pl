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
ms.openlocfilehash: 8874deede8b46b93df0e298fb3970fa153b51415
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396571"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="0553c-102">ICorDebugVariableHome:: getlocationtype — Metoda</span><span class="sxs-lookup"><span data-stu-id="0553c-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="0553c-103">Pobiera typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0553c-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0553c-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0553c-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0553c-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="0553c-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="0553c-106">określoną Wskaźnik do typu lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0553c-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="0553c-107">Aby uzyskać więcej informacji, zobacz Wyliczenie [VariableLocationType](variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="0553c-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0553c-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0553c-108">Requirements</span></span>  
 <span data-ttu-id="0553c-109">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0553c-109">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0553c-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0553c-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0553c-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0553c-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0553c-112">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0553c-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0553c-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0553c-113">See also</span></span>

- [<span data-ttu-id="0553c-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="0553c-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="0553c-115">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0553c-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
