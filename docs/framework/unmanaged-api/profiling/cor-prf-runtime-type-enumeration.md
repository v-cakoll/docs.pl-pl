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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7c3a3581d2a9a1cb79f4ffe1d0a37269c18789a6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54652187"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="86988-102">COR_PRF_RUNTIME_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="86988-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="86988-103">Zawiera wartości, które wskazują wersji środowiska uruchomieniowego języka wspólnego (CLR): pulpicie lub w środowisku CoreCLR, który jest używany w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="86988-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="86988-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="86988-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="86988-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="86988-105">Members</span></span>  
  
|<span data-ttu-id="86988-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="86988-106">Member</span></span>|<span data-ttu-id="86988-107">Opis</span><span class="sxs-lookup"><span data-stu-id="86988-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="86988-108">Klasycznej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="86988-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="86988-109">Wersja core CLR, używany w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="86988-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="86988-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="86988-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="86988-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="86988-111">Requirements</span></span>  
 <span data-ttu-id="86988-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="86988-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="86988-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="86988-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="86988-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="86988-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="86988-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="86988-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86988-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86988-116">See also</span></span>
- [<span data-ttu-id="86988-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="86988-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
