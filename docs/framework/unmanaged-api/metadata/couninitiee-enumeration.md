---
title: "COUNINITIEE — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- COUNINITIEE
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- COUNINITIEE
helpviewer_keywords:
- COUNINITIEE enumeration [.NET Framework metadata]
ms.assetid: c42baa79-f469-4330-95a2-baf7f021c2fc
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 808320a2034011793429f1805edea82a52add23d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="couninitiee-enumeration"></a><span data-ttu-id="6ab90-102">COUNINITIEE — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="6ab90-102">COUNINITIEE Enumeration</span></span>
<span data-ttu-id="6ab90-103">Określa stałe używane przez [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) podczas inicjowania środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="6ab90-103">Specifies constants used by [CoUninitializeEE](../../../../docs/framework/unmanaged-api/hosting/couninitializeee-function.md) when initializing the common language runtime.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ab90-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="6ab90-104">Syntax</span></span>  
  
```  
typedef enum tagCOUNINITEE  
{  
    COUNINITEE_DEFAULT  = 0x0,   
    COUNINITEE_DLL      = 0x1  
} COUNINITIEE;  
```  
  
## <a name="members"></a><span data-ttu-id="6ab90-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="6ab90-105">Members</span></span>  
  
|<span data-ttu-id="6ab90-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="6ab90-106">Member</span></span>|<span data-ttu-id="6ab90-107">Opis</span><span class="sxs-lookup"><span data-stu-id="6ab90-107">Description</span></span>|  
|------------|-----------------|  
|`COUNINITEE_DEFAULT`|<span data-ttu-id="6ab90-108">Określa domyślny tryb uninitialization.</span><span class="sxs-lookup"><span data-stu-id="6ab90-108">Indicates default uninitialization mode.</span></span>|  
|`COUNINITEE_DLL`|<span data-ttu-id="6ab90-109">Wskazuje tryb uninitialization wyładowania zestawu.</span><span class="sxs-lookup"><span data-stu-id="6ab90-109">Indicates uninitialization mode for unloading an assembly.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6ab90-110">Wymagania</span><span class="sxs-lookup"><span data-stu-id="6ab90-110">Requirements</span></span>  
 <span data-ttu-id="6ab90-111">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6ab90-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6ab90-112">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="6ab90-112">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="6ab90-113">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="6ab90-113">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="6ab90-114">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6ab90-114">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ab90-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ab90-115">See Also</span></span>  
 [<span data-ttu-id="6ab90-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="6ab90-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
