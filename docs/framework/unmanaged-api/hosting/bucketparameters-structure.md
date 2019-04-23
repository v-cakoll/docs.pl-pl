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
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59110459"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="75c12-102">BucketParameters — Struktura</span><span class="sxs-lookup"><span data-stu-id="75c12-102">BucketParameters Structure</span></span>
<span data-ttu-id="75c12-103">Przechowuje nazwę typu zdarzenia i parametry dla bieżącego wyjątku, który jest skojarzony ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="75c12-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="75c12-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="75c12-104">Syntax</span></span>  
  
```  
typedef struct _BucketParameters {  
    BOOL  fInited;                    
    WCHAR pszEventTypeName[255];      
    WCHAR pszParams[10][255];         
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="75c12-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="75c12-105">Members</span></span>  
  
|<span data-ttu-id="75c12-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="75c12-106">Member</span></span>|<span data-ttu-id="75c12-107">Opis</span><span class="sxs-lookup"><span data-stu-id="75c12-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="75c12-108">`true`, jeśli pozostałą część tej struktury jest prawidłowy; w przeciwnym razie `false`.</span><span class="sxs-lookup"><span data-stu-id="75c12-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="75c12-109">Nazwa typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="75c12-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="75c12-110">Tablica ciągów, z których każdy określa parametr dla bieżącego wyjątku skojarzonego ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="75c12-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="75c12-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="75c12-111">Requirements</span></span>  
 <span data-ttu-id="75c12-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="75c12-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="75c12-113">**Nagłówek:** MSCorEE.idl</span><span class="sxs-lookup"><span data-stu-id="75c12-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="75c12-114">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="75c12-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="75c12-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="75c12-115">See also</span></span>

- [<span data-ttu-id="75c12-116">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="75c12-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
