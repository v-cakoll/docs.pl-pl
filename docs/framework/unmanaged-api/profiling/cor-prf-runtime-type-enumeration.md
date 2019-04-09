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
ms.openlocfilehash: e57c622780f0bc92061fd2928ea861f904d9eb37
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122112"
---
# <a name="corprfruntimetype-enumeration"></a><span data-ttu-id="0fe55-102">COR_PRF_RUNTIME_TYPE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0fe55-102">COR_PRF_RUNTIME_TYPE Enumeration</span></span>
<span data-ttu-id="0fe55-103">Zawiera wartości, które wskazują wersji środowiska uruchomieniowego języka wspólnego (CLR): pulpicie lub w środowisku CoreCLR, który jest używany w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="0fe55-103">Contains values that indicate the version of the common language runtime (CLR): desktop or CoreCLR, which is used in Silverlight.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0fe55-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0fe55-104">Syntax</span></span>  
  
```  
typedef enum  
{  
    COR_PRF_DESKTOP_CLR = 0x1,  
    COR_PRF_CORE_CLR    = 0x2,  
} COR_PRF_RUNTIME_TYPE;  
```  
  
## <a name="members"></a><span data-ttu-id="0fe55-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="0fe55-105">Members</span></span>  
  
|<span data-ttu-id="0fe55-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0fe55-106">Member</span></span>|<span data-ttu-id="0fe55-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0fe55-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_DESKTOP_CLR`|<span data-ttu-id="0fe55-108">Klasycznej wersji środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="0fe55-108">The desktop version of the CLR.</span></span>|  
|`COR_PRF_CORE_CLR`|<span data-ttu-id="0fe55-109">Wersja core CLR, używany w technologii Silverlight.</span><span class="sxs-lookup"><span data-stu-id="0fe55-109">The core version of the CLR, used in Silverlight.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0fe55-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0fe55-110">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0fe55-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0fe55-111">Requirements</span></span>  
 <span data-ttu-id="0fe55-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0fe55-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0fe55-113">**Nagłówek:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="0fe55-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="0fe55-114">**Biblioteka:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0fe55-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="0fe55-115">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="0fe55-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0fe55-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fe55-116">See also</span></span>

- [<span data-ttu-id="0fe55-117">Profilowanie — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="0fe55-117">Profiling Enumerations</span></span>](../../../../docs/framework/unmanaged-api/profiling/profiling-enumerations.md)
