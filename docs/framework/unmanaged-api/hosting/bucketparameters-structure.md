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
ms.openlocfilehash: 4d9de489bdeb0ab506f56ff08f4afb4cf6d0ab4f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178275"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="f7b18-102">BucketParameters — Struktura</span><span class="sxs-lookup"><span data-stu-id="f7b18-102">BucketParameters Structure</span></span>
<span data-ttu-id="f7b18-103">Przechowuje nazwę typu zdarzenia i parametry dla bieżącego wyjątku, który jest skojarzony ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="f7b18-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7b18-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="f7b18-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="f7b18-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="f7b18-105">Members</span></span>  
  
|<span data-ttu-id="f7b18-106">Członek</span><span class="sxs-lookup"><span data-stu-id="f7b18-106">Member</span></span>|<span data-ttu-id="f7b18-107">Opis</span><span class="sxs-lookup"><span data-stu-id="f7b18-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="f7b18-108">`true`, jeśli pozostała część tej struktury jest ważna; w `false`przeciwnym razie , .</span><span class="sxs-lookup"><span data-stu-id="f7b18-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="f7b18-109">Nazwa typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="f7b18-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="f7b18-110">Tablica ciągów, z których każdy określa parametr dla bieżącego wyjątku skojarzonego ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="f7b18-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="f7b18-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="f7b18-111">Requirements</span></span>  
 <span data-ttu-id="f7b18-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f7b18-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f7b18-113">**Nagłówek:** mscoree.idl</span><span class="sxs-lookup"><span data-stu-id="f7b18-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="f7b18-114">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f7b18-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7b18-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f7b18-115">See also</span></span>

- [<span data-ttu-id="f7b18-116">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="f7b18-116">Hosting Structures</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
