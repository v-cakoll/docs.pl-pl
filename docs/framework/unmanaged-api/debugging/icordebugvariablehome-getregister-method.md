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
ms.openlocfilehash: 7f16e4bfe4767e1b49d7dacf0481e8911a90e178
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="df854-102">ICorDebugVariableHome::GetRegister — metoda</span><span class="sxs-lookup"><span data-stu-id="df854-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="df854-103">Pobiera rejestr, który zawiera zmienną z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="df854-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="df854-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="df854-104">Syntax</span></span>  
  
```  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="df854-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="df854-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="df854-106">[out] Wartość wyliczenia CorDebugRegister, która wskazuje rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER`oraz podstawowej rejestru dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="df854-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="df854-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="df854-107">Return Value</span></span>  
 <span data-ttu-id="df854-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="df854-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="df854-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="df854-109">Value</span></span>|<span data-ttu-id="df854-110">Opis</span><span class="sxs-lookup"><span data-stu-id="df854-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="df854-111">Zmienna jest w rejestrze wskazywanym przez `pRegister` argumentu.</span><span class="sxs-lookup"><span data-stu-id="df854-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="df854-112">Zmienna nie jest w rejestrze lub w lokalizacji rejestru względnego.</span><span class="sxs-lookup"><span data-stu-id="df854-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df854-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="df854-113">Requirements</span></span>  
 <span data-ttu-id="df854-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="df854-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="df854-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="df854-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="df854-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="df854-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="df854-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="df854-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df854-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="df854-118">See Also</span></span>  
 [<span data-ttu-id="df854-119">VariableLocationType — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="df854-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)  
 [<span data-ttu-id="df854-120">Interfejs ICorDebugVariableHome</span><span class="sxs-lookup"><span data-stu-id="df854-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
