---
title: "VariableLocationType — wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
api_name: VariableLocationType
api_location: mscordbi.dll
api_type: COM
f1_keywords: VariableLocationType
helpviewer_keywords: VariableLocationType enumeration [.NET Framework debugging]
ms.assetid: 8635ee3a-c84b-4626-876c-416bee54f787
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0338a89acdd9c29370bc8e52ed9a099e9330c2cc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="variablelocationtype-enumeration"></a><span data-ttu-id="fdd62-102">VariableLocationType — wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fdd62-102">VariableLocationType Enumeration</span></span>
<span data-ttu-id="fdd62-103">Wskazuje typ macierzysty lokalizacji zmiennej.</span><span class="sxs-lookup"><span data-stu-id="fdd62-103">Indicates the native location type of a variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdd62-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fdd62-104">Syntax</span></span>  
  
```  
typedef enum VariableLocationType  
{  
    VLT_REGISTER,               
    VLT_REGISTER_RELATIVE,      
    VLT_INVALID  
} VariableLocationType;  
```  
  
## <a name="members"></a><span data-ttu-id="fdd62-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="fdd62-105">Members</span></span>  
  
|<span data-ttu-id="fdd62-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="fdd62-106">Member</span></span>|<span data-ttu-id="fdd62-107">Opis</span><span class="sxs-lookup"><span data-stu-id="fdd62-107">Description</span></span>|  
|------------|-----------------|  
|`VLT_REGISTER`|<span data-ttu-id="fdd62-108">Zmienna jest w rejestrze.</span><span class="sxs-lookup"><span data-stu-id="fdd62-108">The variable is in a register.</span></span>|  
|`VLT_REGISTER_RELATIVE`|<span data-ttu-id="fdd62-109">Zmienna znajduje się w lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="fdd62-109">The variable is in a register-relative memory location.</span></span>|  
|`VLT_INVALID`|<span data-ttu-id="fdd62-110">Zmienna nie są przechowywane w rejestrze lub lokalizacji pamięci względem rejestru.</span><span class="sxs-lookup"><span data-stu-id="fdd62-110">The variable is not stored in a register or a register-relative memory location.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fdd62-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="fdd62-111">Remarks</span></span>  
 <span data-ttu-id="fdd62-112">Członek `VariableLocationType` wyliczenie jest zwracany przez [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) metody.</span><span class="sxs-lookup"><span data-stu-id="fdd62-112">A member of the `VariableLocationType` enumeration is returned by the [ICorDebugVariableHome::GetLocationType](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-getlocationtype-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fdd62-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fdd62-113">Requirements</span></span>  
 <span data-ttu-id="fdd62-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fdd62-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fdd62-115">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fdd62-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fdd62-116">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fdd62-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fdd62-117">**Wersje programu .NET framework:**[!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fdd62-117">**.NET Framework Versions:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fdd62-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdd62-118">See Also</span></span>  
 [<span data-ttu-id="fdd62-119">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="fdd62-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
