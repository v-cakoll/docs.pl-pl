---
title: ICorDebugVariableHome::GetRegister — metoda
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
ms.openlocfilehash: e06c98067fea9368ac8f750d9187636d2ca9a8c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420111"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="04659-102">ICorDebugVariableHome::GetRegister — metoda</span><span class="sxs-lookup"><span data-stu-id="04659-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="04659-103">Pobiera rejestr, który zawiera zmienną z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="04659-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="04659-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="04659-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="04659-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="04659-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="04659-106">[out] Wartość wyliczenia CorDebugRegister, która wskazuje rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="04659-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="04659-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="04659-107">Return Value</span></span>  
 <span data-ttu-id="04659-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="04659-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="04659-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="04659-109">Value</span></span>|<span data-ttu-id="04659-110">Opis</span><span class="sxs-lookup"><span data-stu-id="04659-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="04659-111">Zmienna jest w rejestrze wskazywanym przez `pRegister` argumentu.</span><span class="sxs-lookup"><span data-stu-id="04659-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="04659-112">Zmienna nie jest w rejestrze lub w lokalizacji rejestru względnego.</span><span class="sxs-lookup"><span data-stu-id="04659-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="04659-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="04659-113">Requirements</span></span>  
 <span data-ttu-id="04659-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="04659-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="04659-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="04659-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="04659-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="04659-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="04659-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="04659-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04659-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="04659-118">See Also</span></span>  
 [<span data-ttu-id="04659-119">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="04659-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="04659-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="04659-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
