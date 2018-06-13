---
title: CorDebugMappingResult — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407962"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="43864-102">CorDebugMappingResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="43864-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="43864-103">Zawiera szczegółowe informacje o sposobie uzyskano wartość wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="43864-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="43864-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="43864-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="43864-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="43864-105">Members</span></span>  
  
|<span data-ttu-id="43864-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="43864-106">Member</span></span>|<span data-ttu-id="43864-107">Opis</span><span class="sxs-lookup"><span data-stu-id="43864-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="43864-108">Kod natywny znajduje się w prologu, więc wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="43864-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="43864-109">Kod natywny jest w epilogu, dlatego wartość adres IP jest adresem ostatniej instrukcji metody.</span><span class="sxs-lookup"><span data-stu-id="43864-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="43864-110">Informacje mapowania są niedostępne w przypadku metody, więc wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="43864-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="43864-111">Ma informacji o mapowaniu dla metody, ale bieżący adres nie można mapować do kodu języka pośredniego (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="43864-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="43864-112">Wartość adresu IP to 0.</span><span class="sxs-lookup"><span data-stu-id="43864-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="43864-113">Metoda mapuje się dokładnie do kodu MSIL albo został zinterpretowany ramki, dlatego wartość adres IP jest dokładne.</span><span class="sxs-lookup"><span data-stu-id="43864-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="43864-114">Metoda został pomyślnie zamapowany, ale wartość adresu IP może być przybliżonej.</span><span class="sxs-lookup"><span data-stu-id="43864-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="43864-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="43864-115">Remarks</span></span>  
 <span data-ttu-id="43864-116">Można użyć [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodę, aby uzyskać wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="43864-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="43864-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="43864-117">Requirements</span></span>  
 <span data-ttu-id="43864-118">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="43864-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="43864-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="43864-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="43864-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="43864-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="43864-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="43864-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43864-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="43864-122">See Also</span></span>  
 [<span data-ttu-id="43864-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="43864-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
