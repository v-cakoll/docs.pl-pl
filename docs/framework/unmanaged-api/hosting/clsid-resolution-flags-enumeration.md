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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bee25122920a6fcec3bbd4e9e53bbdad008d5304
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514116"
---
# <a name="clsidresolutionflags-enumeration"></a><span data-ttu-id="6bf35-102">CLSID_RESOLUTION_FLAGS — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6bf35-102">CLSID_RESOLUTION_FLAGS Enumeration</span></span>
<span data-ttu-id="6bf35-103">Zawiera wartości, które wskazują, jak środowisko uruchomieniowe języka wspólnego (CLR) powinna być rozpoznawana `CLSID`.</span><span class="sxs-lookup"><span data-stu-id="6bf35-103">Contains values that indicate how the common language runtime (CLR) should resolve a `CLSID`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6bf35-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6bf35-104">Syntax</span></span>  
  
```  
typedef enum {  
    CLSID_RESOLUTION_DEFAULT      = 0x0,  
    CLSID_RESOLUTION_REGISTERED   = 0x1  
} CLSID_RESOLUTION_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="6bf35-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6bf35-105">Members</span></span>  
  
|<span data-ttu-id="6bf35-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6bf35-106">Member</span></span>|<span data-ttu-id="6bf35-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6bf35-107">Description</span></span>|  
|------------|-----------------|  
|`CLSID_RESOLUTION_DEFAULT`|<span data-ttu-id="6bf35-108">Wskazuje zachowanie domyślne.</span><span class="sxs-lookup"><span data-stu-id="6bf35-108">Indicates the default behavior.</span></span>|  
|`CLSID_RESOLUTION_REGISTERED`|<span data-ttu-id="6bf35-109">Wskazuje, że środowisko uruchomieniowe wyszukuje rejestru i stosuje zasady podkładki.</span><span class="sxs-lookup"><span data-stu-id="6bf35-109">Indicates that the runtime searches the registry and applies shim policy.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6bf35-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6bf35-110">Requirements</span></span>  
 <span data-ttu-id="6bf35-111">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6bf35-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6bf35-112">**Nagłówek:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="6bf35-112">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="6bf35-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6bf35-113">**.NET Framework Versions:** [!INCLUDE[net_current_v11plus](../../../../includes/net-current-v11plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6bf35-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6bf35-114">See also</span></span>
- [<span data-ttu-id="6bf35-115">Hosting — wyliczenia</span><span class="sxs-lookup"><span data-stu-id="6bf35-115">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
