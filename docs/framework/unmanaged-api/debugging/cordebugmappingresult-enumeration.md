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
ms.openlocfilehash: c2fecc7160cb41e31bf88f1a461265ad8fdce166
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170394"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="f64b6-102">CorDebugMappingResult — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="f64b6-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="f64b6-103">Zawiera szczegółowe informacje, jak uzyskać była wartość wskaźnika instrukcji (IP).</span><span class="sxs-lookup"><span data-stu-id="f64b6-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f64b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f64b6-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="f64b6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f64b6-105">Members</span></span>  
  
|<span data-ttu-id="f64b6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="f64b6-106">Member</span></span>|<span data-ttu-id="f64b6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f64b6-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="f64b6-108">Kod macierzysty znajduje się w prologu, więc wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="f64b6-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="f64b6-109">Natywny kod znajduje się w epilogu, więc wartość adresu IP jest adresem ostatniej instrukcji metody.</span><span class="sxs-lookup"><span data-stu-id="f64b6-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="f64b6-110">Nie informacji o mapowaniu jest dostępna w przypadku metody, więc wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="f64b6-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="f64b6-111">Mimo że istnieje informacje dotyczące mapowania dla metody, bieżący adres nie można zamapować na kod intermediate language (MSIL) firmy Microsoft.</span><span class="sxs-lookup"><span data-stu-id="f64b6-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="f64b6-112">Wartość adresu IP wynosi 0.</span><span class="sxs-lookup"><span data-stu-id="f64b6-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="f64b6-113">Metoda mapuje dokładnie kod MSIL albo ramki jest interpretowany, więc wartość adresu IP jest dokładne.</span><span class="sxs-lookup"><span data-stu-id="f64b6-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="f64b6-114">Metoda został pomyślnie zamapowany, ale wartość adresu IP może być przybliżone.</span><span class="sxs-lookup"><span data-stu-id="f64b6-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f64b6-115">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f64b6-115">Remarks</span></span>  
 <span data-ttu-id="f64b6-116">Możesz użyć [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) metodę, aby uzyskać wartość wskaźnika instrukcji.</span><span class="sxs-lookup"><span data-stu-id="f64b6-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f64b6-117">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f64b6-117">Requirements</span></span>  
 <span data-ttu-id="f64b6-118">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f64b6-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f64b6-119">**Nagłówek:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f64b6-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f64b6-120">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f64b6-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f64b6-121">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f64b6-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f64b6-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f64b6-122">See also</span></span>

- [<span data-ttu-id="f64b6-123">Debugowanie, wyliczenia</span><span class="sxs-lookup"><span data-stu-id="f64b6-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
