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
ms.openlocfilehash: 5d33c917ab814083ec2f3a3f3de6bdc264d90b77
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791010"
---
# <a name="icordebugvariablehomegetlocationtype-method"></a><span data-ttu-id="5230a-102">ICorDebugVariableHome:: getlocationtype — Metoda</span><span class="sxs-lookup"><span data-stu-id="5230a-102">ICorDebugVariableHome::GetLocationType Method</span></span>
<span data-ttu-id="5230a-103">Pobiera typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5230a-103">Gets the type of the variable's native location.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5230a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="5230a-104">Syntax</span></span>  
  
```cpp  
HRESULT GetLocationType(  
    [out] VariableLocationType *pLocationType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="5230a-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="5230a-105">Parameters</span></span>  
 `pLocationType`  
 <span data-ttu-id="5230a-106">określoną Wskaźnik do typu lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="5230a-106">[out] A pointer to the type of the variable's native location.</span></span>  <span data-ttu-id="5230a-107">Aby uzyskać więcej informacji, zobacz Wyliczenie [VariableLocationType](variablelocationtype-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="5230a-107">See the [VariableLocationType](variablelocationtype-enumeration.md) enumeration for more information.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="5230a-108">Wymagania</span><span class="sxs-lookup"><span data-stu-id="5230a-108">Requirements</span></span>  
 <span data-ttu-id="5230a-109">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5230a-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5230a-110">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="5230a-110">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="5230a-111">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="5230a-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="5230a-112">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5230a-112">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5230a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5230a-113">See also</span></span>

- [<span data-ttu-id="5230a-114">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="5230a-114">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
- [<span data-ttu-id="5230a-115">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="5230a-115">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
