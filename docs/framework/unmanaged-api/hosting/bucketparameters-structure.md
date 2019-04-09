---
title: BucketParameters — Struktura
ms.date: 03/30/2017
api_name:
- BucketParameters
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- BucketParameters
helpviewer_keywords:
- BucketParameters structure [.NET Framework hosting]
ms.assetid: 9432487e-f276-45d6-9a13-9a68024dbd46
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5998ce684726b2386d8f1e05eb7eaeccf455747c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110459"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="73b80-102">BucketParameters — Struktura</span><span class="sxs-lookup"><span data-stu-id="73b80-102">BucketParameters Structure</span></span>
<span data-ttu-id="73b80-103">Przechowuje nazwę typu zdarzenia i parametry dla bieżącego wyjątku, który jest skojarzony ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="73b80-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="73b80-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="73b80-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="73b80-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="73b80-105">Members</span></span>  
  
|<span data-ttu-id="73b80-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="73b80-106">Member</span></span>|<span data-ttu-id="73b80-107">Opis</span><span class="sxs-lookup"><span data-stu-id="73b80-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|`true`<span data-ttu-id="73b80-108">, jeśli pozostałą część tej struktury jest prawidłowy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="73b80-108">, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="73b80-109">Nazwa typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="73b80-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="73b80-110">Tablica ciągów, z których każdy określa parametr dla bieżącego wyjątku skojarzonego ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="73b80-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73b80-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="73b80-111">Requirements</span></span>  
 <span data-ttu-id="73b80-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73b80-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73b80-113">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="73b80-113">**Header:** MSCorEE.idl</span></span>  
  
 **<span data-ttu-id="73b80-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="73b80-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="73b80-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="73b80-115">See also</span></span>

- [<span data-ttu-id="73b80-116">Hosting — Struktury</span><span class="sxs-lookup"><span data-stu-id="73b80-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
