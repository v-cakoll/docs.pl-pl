---
title: "ICorDebugVariableHome::GetRegister — metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: ICorDebugVariableHome.GetRegister
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugVariableHome::GetRegister
helpviewer_keywords:
- ICorDebugVariableHome::GetRegister method [.NET Framework debugging]
- GetRegister method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: a5eecd7b-b04c-4266-bff2-7c8771d519a8
topic_type: apiref
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 54f1c737b0c6ce6281a71419cbd8c88277702f41
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="dd838-102">ICorDebugVariableHome::GetRegister — metoda</span><span class="sxs-lookup"><span data-stu-id="dd838-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="dd838-103">Pobiera rejestr, który zawiera zmienną z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="dd838-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd838-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="dd838-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="dd838-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="dd838-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="dd838-106">[out] Wartość wyliczenia CorDebugRegister, która wskazuje rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="dd838-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="dd838-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="dd838-107">Return Value</span></span>  
 <span data-ttu-id="dd838-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="dd838-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="dd838-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="dd838-109">Value</span></span>|<span data-ttu-id="dd838-110">Opis</span><span class="sxs-lookup"><span data-stu-id="dd838-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="dd838-111">Zmienna jest w rejestrze wskazywanym przez `pRegister` argumentu.</span><span class="sxs-lookup"><span data-stu-id="dd838-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="dd838-112">Zmienna nie jest w rejestrze lub w lokalizacji rejestru względnego.</span><span class="sxs-lookup"><span data-stu-id="dd838-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="dd838-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="dd838-113">Requirements</span></span>  
 <span data-ttu-id="dd838-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="dd838-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="dd838-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="dd838-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="dd838-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="dd838-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="dd838-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="dd838-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dd838-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="dd838-118">See Also</span></span>  
 [<span data-ttu-id="dd838-119">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="dd838-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="dd838-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="dd838-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
