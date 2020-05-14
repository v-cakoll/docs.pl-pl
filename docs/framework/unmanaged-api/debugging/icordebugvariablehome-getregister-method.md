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
ms.openlocfilehash: 6cf66774209bd07426872c29c15b2225421c2b4d
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396830"
---
# <a name="icordebugvariablehomegetregister-method"></a><span data-ttu-id="3ba43-102">ICorDebugVariableHome:: getregister — Metoda</span><span class="sxs-lookup"><span data-stu-id="3ba43-102">ICorDebugVariableHome::GetRegister Method</span></span>
<span data-ttu-id="3ba43-103">Pobiera rejestr zawierający zmienną z typem lokalizacji `VLT_REGISTER` i rejestr podstawowy dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="3ba43-103">Gets the register that contains a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3ba43-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3ba43-104">Syntax</span></span>  
  
```cpp  
HRESULT GetRegister(  
    [out] CorDebugRegister *pRegister  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3ba43-105">Parametry</span><span class="sxs-lookup"><span data-stu-id="3ba43-105">Parameters</span></span>  
 `pRegister`  
 <span data-ttu-id="3ba43-106">określoną Wartość wyliczenia CorDebugRegister —, która wskazuje rejestr dla zmiennej z typem lokalizacji `VLT_REGISTER` i rejestr podstawowy dla zmiennej z typem lokalizacji `VLT_REGISTER_RELATIVE` .</span><span class="sxs-lookup"><span data-stu-id="3ba43-106">[out] A CorDebugRegister enumeration value  that indicates the register for a variable with a location type of `VLT_REGISTER`, and the base register for a variable with a location type of `VLT_REGISTER_RELATIVE`.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3ba43-107">Wartość zwracana</span><span class="sxs-lookup"><span data-stu-id="3ba43-107">Return Value</span></span>  
 <span data-ttu-id="3ba43-108">Metoda zwraca następujące wartości:</span><span class="sxs-lookup"><span data-stu-id="3ba43-108">The method returns the following values:</span></span>  
  
|<span data-ttu-id="3ba43-109">Wartość</span><span class="sxs-lookup"><span data-stu-id="3ba43-109">Value</span></span>|<span data-ttu-id="3ba43-110">Opis</span><span class="sxs-lookup"><span data-stu-id="3ba43-110">Description</span></span>|  
|-----------|-----------------|  
|`S_OK`|<span data-ttu-id="3ba43-111">Zmienna znajduje się w rejestrze wskazanym przez `pRegister` argument.</span><span class="sxs-lookup"><span data-stu-id="3ba43-111">The variable is in the register indicated by the `pRegister` argument.</span></span>|  
|`E_FAIL`|<span data-ttu-id="3ba43-112">Zmienna nie znajduje się w rejestrze ani w lokalizacji względnej do rejestracji.</span><span class="sxs-lookup"><span data-stu-id="3ba43-112">The variable is not in a register or a register-relative location.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3ba43-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3ba43-113">Requirements</span></span>  
 <span data-ttu-id="3ba43-114">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3ba43-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3ba43-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="3ba43-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3ba43-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="3ba43-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3ba43-117">**.NET Framework wersje:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3ba43-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3ba43-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="3ba43-118">See also</span></span>

- [<span data-ttu-id="3ba43-119">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3ba43-119">VariableLocationType Enumeration</span></span>](variablelocationtype-enumeration.md)
- [<span data-ttu-id="3ba43-120">ICorDebugVariableHome, interfejs</span><span class="sxs-lookup"><span data-stu-id="3ba43-120">ICorDebugVariableHome Interface</span></span>](icordebugvariablehome-interface.md)
