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
ms.openlocfilehash: ddb5af486ab6fb1c8c4fabf3ccf7b43d037e1eeb
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789320"
---
# <a name="cordebugiltonativemappingtypes-enumeration"></a><span data-ttu-id="93a3e-102">CorDebugIlToNativeMappingTypes — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="93a3e-102">CorDebugIlToNativeMappingTypes Enumeration</span></span>
<span data-ttu-id="93a3e-103">Wskazuje, czy konkretny zakres instrukcji macierzystych, reprezentowany przez wystąpienie struktury COR_DEBUG_IL_TO_NATIVE_MAP, odpowiada specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="93a3e-103">Indicates whether a particular range of native instructions, represented by an instance of the COR_DEBUG_IL_TO_NATIVE_MAP structure, corresponds to a special code region.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="93a3e-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="93a3e-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugIlToNativeMappingTypes {  
    NO_MAPPING = -1,  
    PROLOG     = -2,  
    EPILOG     = -3  
} CorDebugIlToNativeMappingTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="93a3e-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="93a3e-105">Members</span></span>  
  
|<span data-ttu-id="93a3e-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="93a3e-106">Member</span></span>|<span data-ttu-id="93a3e-107">Opis</span><span class="sxs-lookup"><span data-stu-id="93a3e-107">Description</span></span>|  
|------------|-----------------|  
|`NO_MAPPING`|<span data-ttu-id="93a3e-108">Zakres instrukcji natywnych nie odpowiada żadnemu specjalnemu regionowi kodu.</span><span class="sxs-lookup"><span data-stu-id="93a3e-108">The range of native instructions does not correspond to any special code region.</span></span>|  
|`PROLOG`|<span data-ttu-id="93a3e-109">Zakres natywnych instrukcji odpowiada prologu.</span><span class="sxs-lookup"><span data-stu-id="93a3e-109">The range of native instructions corresponds to the prolog.</span></span>|  
|`EPILOG`|<span data-ttu-id="93a3e-110">Zakres instrukcji natywnych odpowiada epilogu.</span><span class="sxs-lookup"><span data-stu-id="93a3e-110">The range of native instructions corresponds to the epilog.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="93a3e-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="93a3e-111">Requirements</span></span>  
 <span data-ttu-id="93a3e-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="93a3e-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="93a3e-113">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="93a3e-113">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="93a3e-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="93a3e-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="93a3e-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="93a3e-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="93a3e-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="93a3e-116">See also</span></span>

- [<span data-ttu-id="93a3e-117">GetILToNativeMapping, metoda</span><span class="sxs-lookup"><span data-stu-id="93a3e-117">GetILToNativeMapping Method</span></span>](icordebugcode-getiltonativemapping-method.md)
- [<span data-ttu-id="93a3e-118">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="93a3e-118">Debugging Enumerations</span></span>](debugging-enumerations.md)
