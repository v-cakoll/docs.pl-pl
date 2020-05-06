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
ms.openlocfilehash: 808fc70a308eff1b05aa49ea2bb89fe53377c973
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795849"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="40f5a-102">CorDebugIlToNativeMappingTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="40f5a-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="40f5a-103">Wskazuje, czy konkretny zakres instrukcji macierzystych, reprezentowany przez wystąpienie struktury COR_DEBUG_IL_TO_NATIVE_MAP, odpowiada specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="40f5a-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="40f5a-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="40f5a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="40f5a-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="40f5a-105">Members</span></span>  
  
|<span data-ttu-id="40f5a-106">Członek</span><span class="sxs-lookup"><span data-stu-id="40f5a-106">Member</span></span>|<span data-ttu-id="40f5a-107">Opis</span><span class="sxs-lookup"><span data-stu-id="40f5a-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="40f5a-108">Zakres instrukcji natywnych nie odpowiada żadnemu specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="40f5a-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="40f5a-109">Zakres natywnych instrukcji odpowiada prologu.</span><span class="sxs-lookup"><span data-stu-id="40f5a-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="40f5a-110">Zakres instrukcji natywnych odpowiada epilogu.</span><span class="sxs-lookup"><span data-stu-id="40f5a-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="40f5a-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="40f5a-111">Requirements</span></span>  
 <span data-ttu-id="40f5a-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="40f5a-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="40f5a-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="40f5a-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="40f5a-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="40f5a-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="40f5a-115">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="40f5a-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40f5a-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="40f5a-116">See also</span></span>

- [<span data-ttu-id="40f5a-117">GetILToNativeMapping — Metoda</span><span class="sxs-lookup"><span data-stu-id="40f5a-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="40f5a-118">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="40f5a-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
