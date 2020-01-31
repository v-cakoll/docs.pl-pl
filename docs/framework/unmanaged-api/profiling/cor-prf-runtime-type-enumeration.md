---
title: COR_PRF_RUNTIME_TYPE — Wyliczenie
ms.date: 03/30/2017
api_name:
- COR_PRF_RUNTIME_TYPE Enumeration
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_RUNTIME_TYPE
helpviewer_keywords:
- COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type:
- apiref
ms.openlocfilehash: c1767e718e597918ef59b72a4b7acc3589421de0
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867059"
---
# <a name="cor_prf_runtime_type-enumeration"></a><span data-ttu-id="1de63-102">COR_PRF_RUNTIME_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="1de63-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="1de63-103">Zawiera wartości wskazujące wersję środowiska uruchomieniowego języka wspólnego (CLR): Desktop lub CoreCLR, która jest używana w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="1de63-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1de63-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1de63-104">Syntax</span></span>  
  
```cpp  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="1de63-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1de63-105">Members</span></span>  
  
|<span data-ttu-id="1de63-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1de63-106">Member</span></span>|<span data-ttu-id="1de63-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1de63-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="1de63-108">Wersja klasyczna środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="1de63-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="1de63-109">Wersja podstawowa środowiska CLR używana w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="1de63-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1de63-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1de63-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1de63-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1de63-111">Requirements</span></span>  
 <span data-ttu-id="1de63-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1de63-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1de63-113">**Nagłówek:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="1de63-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1de63-114">**Biblioteka:** CorGuids. lib</span><span class="sxs-lookup"><span data-stu-id="1de63-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1de63-115">**Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1de63-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1de63-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1de63-116">See also</span></span>

- [<span data-ttu-id="1de63-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="1de63-117">Profiling Enumerations</span></span>](profiling-enumerations.md)
