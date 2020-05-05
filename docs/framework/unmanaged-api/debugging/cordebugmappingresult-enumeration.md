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
ms.openlocfilehash: a7a450e85f7eaa765766ffa985d7c01538e2669c
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795797"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="72415-102">CorDebugMappingResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="72415-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="72415-103">Zawiera szczegółowe informacje o sposobie uzyskiwania wartości wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="72415-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="72415-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="72415-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="72415-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="72415-105">Members</span></span>  
  
|<span data-ttu-id="72415-106">Członek</span><span class="sxs-lookup"><span data-stu-id="72415-106">Member</span></span>|<span data-ttu-id="72415-107">Opis</span><span class="sxs-lookup"><span data-stu-id="72415-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="72415-108">Kod natywny znajduje się w prologu, więc wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="72415-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="72415-109">Kod natywny znajduje się w epilogu, więc wartość adresu IP jest adresem ostatniej instrukcji metody.</span><span class="sxs-lookup"><span data-stu-id="72415-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="72415-110">Dla metody nie są dostępne żadne informacje o mapowaniu, dlatego wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="72415-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="72415-111">Chociaż istnieją informacje dotyczące mapowania dla metody, nie można zamapować bieżącego adresu na kod języka pośredniego firmy Microsoft (MSIL).</span><span class="sxs-lookup"><span data-stu-id="72415-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="72415-112">Wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="72415-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="72415-113">Metoda jest mapowana dokładnie na kod MSIL lub ramka została zinterpretowana, więc wartość adresu IP jest dokładna.</span><span class="sxs-lookup"><span data-stu-id="72415-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="72415-114">Metoda została pomyślnie zmapowana, ale wartość adresu IP może być przybliżona.</span><span class="sxs-lookup"><span data-stu-id="72415-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="72415-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="72415-115">Remarks</span></span>  
 <span data-ttu-id="72415-116">Aby uzyskać wartość wskaźnika instrukcji, można użyć metody [ICorDebugILFrame:: GetIP —](icordebugilframe-getip-method.md) .</span><span class="sxs-lookup"><span data-stu-id="72415-116">You can use the [ICorDebugILFrame::GetIP](icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="72415-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="72415-117">Requirements</span></span>  
 <span data-ttu-id="72415-118">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="72415-118">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="72415-119">**Nagłówek:** CorDebug. idl, CorDebug. h</span><span class="sxs-lookup"><span data-stu-id="72415-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="72415-120">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="72415-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="72415-121">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="72415-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="72415-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="72415-122">See also</span></span>

- [<span data-ttu-id="72415-123">Debugowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="72415-123">Debugging Enumerations</span></span>](debugging-enumerations.md)
