---
title: VariableLocationType — wyliczenie
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
ms.openlocfilehash: 1cc7a299e6be328095c0368acf0a4b767fb74d01
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="61680-102">VariableLocationType — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="61680-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="61680-103">Wskazuje typ macierzysty lokalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="61680-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="61680-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="61680-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="61680-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="61680-105">Members</span></span>  
  
|<span data-ttu-id="61680-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="61680-106">Member</span></span>|<span data-ttu-id="61680-107">Opis</span><span class="sxs-lookup"><span data-stu-id="61680-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="61680-108">Zmienna jest w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="61680-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="61680-109">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="61680-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="61680-110">Zmienna nie są przechowywane w rejestrze lub lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="61680-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="61680-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="61680-111">Remarks</span></span>  
 <span data-ttu-id="61680-112">Członek `VariableLocationType` wyliczenie jest zwracany przez [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="61680-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="61680-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="61680-113">Requirements</span></span>  
 <span data-ttu-id="61680-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="61680-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="61680-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="61680-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="61680-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="61680-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="61680-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="61680-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="61680-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="61680-118">See Also</span></span>  
 [<span data-ttu-id="61680-119">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="61680-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
