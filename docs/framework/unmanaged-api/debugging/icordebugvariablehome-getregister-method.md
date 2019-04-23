---
title: ICorDebugVariableHome::GetRegister Method
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetRegister
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 290647f0e0dcaeae53362762ed7f8e0c2f05a82c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59189953"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="db325-102">ICorDebugVariableHome::GetRegister Method</span><span class="sxs-lookup"><span data-stu-id="db325-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="db325-103">Pobiera rejestr, który zawiera zmienną typu lokalizacji `VLT_REGISTER`oraz podstawowego rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="db325-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="db325-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="db325-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="db325-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="db325-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="db325-106">[out] Wartość wyliczenia cordebugregister —, która wskazuje rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER`oraz podstawowego rejestru dla zmiennej o typie lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="db325-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="db325-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="db325-107">Return Value</span></span>  
 <span data-ttu-id="db325-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="db325-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="db325-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="db325-109">Value</span></span>|<span data-ttu-id="db325-110">Opis</span><span class="sxs-lookup"><span data-stu-id="db325-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="db325-111">Zmienna jest w rejestrze, wskazywanym przez `pRegister` argumentu.</span><span class="sxs-lookup"><span data-stu-id="db325-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="db325-112">Zmienna nie jest w rejestrze lub w lokalizacji rejestru powiązane z wątkiem.</span><span class="sxs-lookup"><span data-stu-id="db325-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="db325-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="db325-113">Requirements</span></span>  
 <span data-ttu-id="db325-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="db325-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="db325-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="db325-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="db325-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="db325-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="db325-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="db325-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="db325-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="db325-118">See also</span></span>

- [<span data-ttu-id="db325-119">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="db325-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="db325-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="db325-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
