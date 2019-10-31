---
title: VariableLocationType, wyliczenie
ms.date: 03/30/2017
api_name:
- VariableLocationType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- VariableLocationType
helpviewer_keywords:
- VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type:
- apiref
ms.openlocfilehash: 861d5daa481132d3d6527e8d5fbccfab6436c5fe
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139120"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="0b39e-102">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0b39e-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="0b39e-103">Wskazuje typ lokalizacji natywnej zmiennej.</span><span class="sxs-lookup"><span data-stu-id="0b39e-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0b39e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0b39e-104">Syntax</span></span>  
  
```cpp  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="0b39e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0b39e-105">Members</span></span>  
  
|<span data-ttu-id="0b39e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0b39e-106">Member</span></span>|<span data-ttu-id="0b39e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0b39e-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="0b39e-108">Zmienna jest w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="0b39e-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="0b39e-109">Zmienna znajduje się w lokalizacji pamięci względnej do rejestracji.</span><span class="sxs-lookup"><span data-stu-id="0b39e-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="0b39e-110">Zmienna nie jest przechowywana w rejestrze ani w lokalizacji pamięci względnej dla rejestru.</span><span class="sxs-lookup"><span data-stu-id="0b39e-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0b39e-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0b39e-111">Remarks</span></span>  
 <span data-ttu-id="0b39e-112">Element członkowski wyliczenia `VariableLocationType` jest zwracany przez metodę [ICorDebugVariableHome:: Getlocationtype](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) .</span><span class="sxs-lookup"><span data-stu-id="0b39e-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0b39e-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0b39e-113">Requirements</span></span>  
 <span data-ttu-id="0b39e-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0b39e-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0b39e-115">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="0b39e-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0b39e-116">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="0b39e-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0b39e-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0b39e-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0b39e-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0b39e-118">See also</span></span>

- [<span data-ttu-id="0b39e-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0b39e-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
