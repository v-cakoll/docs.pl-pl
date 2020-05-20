---
title: CLSID_RESOLUTION_FLAGS — Wyliczenie
ms.date: 03/30/2017
api_name:
- CLSID_RESOLUTION_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLSID_RESOLUTION_FLAGS
helpviewer_keywords:
- CLSID_RESOLUTION_FLAGS enumeration [.NET Framework hosting]
ms.assetid: cd8b9879-962a-4811-aa46-2e2b6bae0d84
topic_type:
- apiref
ms.openlocfilehash: 5ac015f958d9504bbd14a66ead86548b8df32764
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616778"
---
# <a name="clsid_resolution_flags-enumeration"></a><span data-ttu-id="8c801-102">CLSID_RESOLUTION_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="8c801-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="8c801-103">Zawiera wartości wskazujące sposób, w jaki środowisko uruchomieniowe języka wspólnego (CLR) powinno rozwiązać problem `CLSID` .</span><span class="sxs-lookup"><span data-stu-id="8c801-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8c801-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="8c801-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="8c801-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="8c801-105">Members</span></span>  
  
|<span data-ttu-id="8c801-106">Członek</span><span class="sxs-lookup"><span data-stu-id="8c801-106">Member</span></span>|<span data-ttu-id="8c801-107">Opis</span><span class="sxs-lookup"><span data-stu-id="8c801-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="8c801-108">Wskazuje zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="8c801-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="8c801-109">Wskazuje, że środowisko uruchomieniowe przeszukuje rejestr i stosuje zasady dotyczące podkładek.</span><span class="sxs-lookup"><span data-stu-id="8c801-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="8c801-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="8c801-110">Requirements</span></span>  
 <span data-ttu-id="8c801-111">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8c801-111">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8c801-112">**Nagłówek:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="8c801-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="8c801-113">**.NET Framework wersje:**[!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8c801-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c801-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8c801-114">See also</span></span>

- [<span data-ttu-id="8c801-115">Hosting — Wyliczenia</span><span class="sxs-lookup"><span data-stu-id="8c801-115">Hosting Enumerations</span></span>](hosting-enumerations.md)
