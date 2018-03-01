---
title: "CorDebugIlToNativeMappingTypes — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorDebugIlToNativeMappingTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugIlToNativeMappingTypes
helpviewer_keywords:
- CorDebugIIToNativeMappingTypes enumeration [.NET Framework debugging]
ms.assetid: c35e2919-42c3-4ba0-ae28-443c35f66f93
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 44546c8d66eff111b70673ed63ab82d30fea0b6d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="568c3-102">CorDebugIlToNativeMappingTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="568c3-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="568c3-103">Wskazuje, czy określony zakres instrukcje macierzystego, reprezentowany przez wystąpienie cor_debug_il_to_native_map — struktura, odpowiada specjalne kodu regionu.</span><span class="sxs-lookup"><span data-stu-id="568c3-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="568c3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="568c3-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="568c3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="568c3-105">Members</span></span>  
  
|<span data-ttu-id="568c3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="568c3-106">Member</span></span>|<span data-ttu-id="568c3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="568c3-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="568c3-108">Zakres natywnego instrukcje nie odpowiada wszelkie specjalne kodu regionu.</span><span class="sxs-lookup"><span data-stu-id="568c3-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="568c3-109">Zakres natywnego instrukcje odpowiada prologu.</span><span class="sxs-lookup"><span data-stu-id="568c3-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="568c3-110">Zakres natywnego instrukcje odpowiada epilogu.</span><span class="sxs-lookup"><span data-stu-id="568c3-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="568c3-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="568c3-111">Requirements</span></span>  
 <span data-ttu-id="568c3-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="568c3-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="568c3-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="568c3-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="568c3-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="568c3-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="568c3-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="568c3-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="568c3-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="568c3-116">See Also</span></span>  
 [<span data-ttu-id="568c3-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="568c3-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)  
 [<span data-ttu-id="568c3-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="568c3-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
