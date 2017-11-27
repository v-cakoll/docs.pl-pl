---
title: "COR_PRF_RUNTIME_TYPE — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_RUNTIME_TYPE Enumeration
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_RUNTIME_TYPE
helpviewer_keywords: COR_PRF_RUNTIME_TYPE enumeration [.NET Framework profiling]
ms.assetid: 35449514-333f-4918-9c60-7aa198d655d2
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1a16cfe2f0f2c05721be4d4630729cfbbff98c8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="2d1b6-102">COR_PRF_RUNTIME_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="2d1b6-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="2d1b6-103">Zawiera wartości, które wskazują wersji środowisko uruchomieniowe języka wspólnego (CLR): pulpitu lub środowisko CoreCLR, który jest używany w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2d1b6-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2d1b6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="2d1b6-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="2d1b6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="2d1b6-105">Members</span></span>  
  
|<span data-ttu-id="2d1b6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="2d1b6-106">Member</span></span>|<span data-ttu-id="2d1b6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="2d1b6-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="2d1b6-108">Tej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="2d1b6-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="2d1b6-109">Wersja core CLR, używany w programie Silverlight.</span><span class="sxs-lookup"><span data-stu-id="2d1b6-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2d1b6-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="2d1b6-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2d1b6-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2d1b6-111">Requirements</span></span>  
 <span data-ttu-id="2d1b6-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2d1b6-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2d1b6-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2d1b6-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2d1b6-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2d1b6-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2d1b6-115">**Wersje programu .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2d1b6-115">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2d1b6-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2d1b6-116">See Also</span></span>  
 [<span data-ttu-id="2d1b6-117">Profilowanie — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="2d1b6-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
