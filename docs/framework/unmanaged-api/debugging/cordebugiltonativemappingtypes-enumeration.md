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
ms.openlocfilehash: 61b57d534770c6ab7cacbc2c084ac364dc31863f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717613"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="29e50-102">CorDebugIlToNativeMappingTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="29e50-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="29e50-103">Wskazuje, czy określony zakres natywne instrukcje, reprezentowany przez wystąpienie cor_debug_il_to_native_map — struktura, odnosi się do regionu specjalny kod.</span><span class="sxs-lookup"><span data-stu-id="29e50-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29e50-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="29e50-104">Syntax</span></span>  
  
```  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="29e50-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="29e50-105">Members</span></span>  
  
|<span data-ttu-id="29e50-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="29e50-106">Member</span></span>|<span data-ttu-id="29e50-107">Opis</span><span class="sxs-lookup"><span data-stu-id="29e50-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="29e50-108">Zakres natywne instrukcje nie odpowiada dowolny region specjalny kod.</span><span class="sxs-lookup"><span data-stu-id="29e50-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="29e50-109">Zakres natywne instrukcje odpowiada prologu.</span><span class="sxs-lookup"><span data-stu-id="29e50-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="29e50-110">Zakres natywne instrukcje odpowiada epilogu.</span><span class="sxs-lookup"><span data-stu-id="29e50-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="29e50-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="29e50-111">Requirements</span></span>  
 <span data-ttu-id="29e50-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="29e50-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="29e50-113">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="29e50-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="29e50-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="29e50-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="29e50-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="29e50-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29e50-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="29e50-116">See also</span></span>
- [<span data-ttu-id="29e50-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="29e50-117">GetILToNativeMapping Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="29e50-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="29e50-118">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
