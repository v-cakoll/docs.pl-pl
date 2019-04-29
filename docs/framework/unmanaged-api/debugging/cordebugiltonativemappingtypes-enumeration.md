---
title: CorDebugIlToNativeMappingTypes — Wyliczenie
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2f62707fb1e52a96cf3f131e9c11fee82ab03f4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61651769"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="7f6b5-102">CorDebugIlToNativeMappingTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="7f6b5-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="7f6b5-103">Wskazuje, czy określony zakres natywne instrukcje, reprezentowany przez wystąpienie cor_debug_il_to_native_map — struktura, odnosi się do regionu specjalny kod.</span><span class="sxs-lookup"><span data-stu-id="7f6b5-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f6b5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="7f6b5-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="7f6b5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="7f6b5-105">Members</span></span>  
  
|<span data-ttu-id="7f6b5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="7f6b5-106">Member</span></span>|<span data-ttu-id="7f6b5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="7f6b5-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="7f6b5-108">Zakres natywne instrukcje nie odpowiada dowolny region specjalny kod.</span><span class="sxs-lookup"><span data-stu-id="7f6b5-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="7f6b5-109">Zakres natywne instrukcje odpowiada prologu.</span><span class="sxs-lookup"><span data-stu-id="7f6b5-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="7f6b5-110">Zakres natywne instrukcje odpowiada epilogu.</span><span class="sxs-lookup"><span data-stu-id="7f6b5-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="7f6b5-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7f6b5-111">Requirements</span></span>  
 <span data-ttu-id="7f6b5-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7f6b5-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7f6b5-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="7f6b5-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="7f6b5-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7f6b5-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7f6b5-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7f6b5-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f6b5-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f6b5-116">See also</span></span>

- [<span data-ttu-id="7f6b5-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="7f6b5-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="7f6b5-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="7f6b5-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
