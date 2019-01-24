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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd1a622faa095836a3d5c22c7a18084482074c2c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653219"
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="9ca78-102">VariableLocationType, wyliczenie</span><span class="sxs-lookup"><span data-stu-id="9ca78-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="9ca78-103">Wskazuje typ lokalizacji natywnych zmienną.</span><span class="sxs-lookup"><span data-stu-id="9ca78-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9ca78-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9ca78-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="9ca78-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9ca78-105">Members</span></span>  
  
|<span data-ttu-id="9ca78-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9ca78-106">Member</span></span>|<span data-ttu-id="9ca78-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9ca78-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="9ca78-108">Zmienna jest w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="9ca78-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="9ca78-109">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="9ca78-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="9ca78-110">Zmienna nie są przechowywane w rejestrze lub lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="9ca78-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9ca78-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9ca78-111">Remarks</span></span>  
 <span data-ttu-id="9ca78-112">Członek `VariableLocationType` wyliczenia jest zwracany przez [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="9ca78-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9ca78-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9ca78-113">Requirements</span></span>  
 <span data-ttu-id="9ca78-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9ca78-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9ca78-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9ca78-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9ca78-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9ca78-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9ca78-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9ca78-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9ca78-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ca78-118">See also</span></span>
- [<span data-ttu-id="9ca78-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="9ca78-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
