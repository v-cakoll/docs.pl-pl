---
title: 'ICorDebugVariableHome:: getregister — Metoda'
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
ms.openlocfilehash: 4c9932c3eeebd0101ee364c9b4d0b0a26862c4b1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73125076"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="6fa2f-102">ICorDebugVariableHome:: getregister — Metoda</span><span class="sxs-lookup"><span data-stu-id="6fa2f-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="6fa2f-103">Pobiera rejestr zawierający zmienną z typem lokalizacji `VLT_REGISTER`i podstawową rejestracją dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="6fa2f-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6fa2f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6fa2f-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6fa2f-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="6fa2f-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="6fa2f-106">określoną Wartość wyliczenia CorDebugRegister —, która wskazuje rejestr dla zmiennej z typem lokalizacji `VLT_REGISTER`i podstawowy rejestr dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE`.</span><span class="sxs-lookup"><span data-stu-id="6fa2f-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6fa2f-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="6fa2f-107">Return Value</span></span>  
 <span data-ttu-id="6fa2f-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="6fa2f-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="6fa2f-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="6fa2f-109">Value</span></span>|<span data-ttu-id="6fa2f-110">Opis</span><span class="sxs-lookup"><span data-stu-id="6fa2f-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="6fa2f-111">Zmienna znajduje się w rejestrze wskazanym przez argument `pRegister`.</span><span class="sxs-lookup"><span data-stu-id="6fa2f-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="6fa2f-112">Zmienna nie znajduje się w rejestrze ani w lokalizacji względnej do rejestracji.</span><span class="sxs-lookup"><span data-stu-id="6fa2f-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6fa2f-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6fa2f-113">Requirements</span></span>  
 <span data-ttu-id="6fa2f-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6fa2f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6fa2f-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="6fa2f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6fa2f-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="6fa2f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6fa2f-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6fa2f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6fa2f-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6fa2f-118">See also</span></span>

- [<span data-ttu-id="6fa2f-119">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6fa2f-119">VariableLocationType Enumeration</span></span>](../../../../docs/framework/unmanaged-api/debugging/variablelocationtype-enumeration.md)
- [<span data-ttu-id="6fa2f-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="6fa2f-120">ICorDebugVariableHome Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
