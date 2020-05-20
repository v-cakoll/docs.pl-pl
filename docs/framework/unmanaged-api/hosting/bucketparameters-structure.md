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
ms.openlocfilehash: 7037065be138c369b847e7f86de7b46fc5ae601a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/19/2020
ms.locfileid: "83616882"
---
# <a name="bucketparameters-structure"></a><span data-ttu-id="e8ae7-102">BucketParameters — Struktura</span><span class="sxs-lookup"><span data-stu-id="e8ae7-102">BucketParameters Structure</span></span>
<span data-ttu-id="e8ae7-103">Przechowuje nazwę typu zdarzenia i parametry bieżącego wyjątku, który jest skojarzony ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="e8ae7-103">Stores the type name of an event and the parameters for the current exception that is associated with the event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8ae7-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="e8ae7-104">Syntax</span></span>  
  
```cpp  
typedef struct _BucketParameters {  
    BOOL  fInited;
    WCHAR pszEventTypeName[255];
    WCHAR pszParams[10][255];
} BucketParameters;  
```  
  
## <a name="members"></a><span data-ttu-id="e8ae7-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="e8ae7-105">Members</span></span>  
  
|<span data-ttu-id="e8ae7-106">Członek</span><span class="sxs-lookup"><span data-stu-id="e8ae7-106">Member</span></span>|<span data-ttu-id="e8ae7-107">Opis</span><span class="sxs-lookup"><span data-stu-id="e8ae7-107">Description</span></span>|  
|------------|-----------------|  
|`fInited`|<span data-ttu-id="e8ae7-108">`true`, jeśli pozostała część tej struktury jest prawidłowa; w przeciwnym razie `false` .</span><span class="sxs-lookup"><span data-stu-id="e8ae7-108">`true`, if the rest of this structure is valid; otherwise, `false`.</span></span>|  
|`pszEventTypeName`|<span data-ttu-id="e8ae7-109">Nazwa typu zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="e8ae7-109">Name of the event type.</span></span>|  
|`pszParams`|<span data-ttu-id="e8ae7-110">Tablica ciągów, z których każdy określa parametr dla bieżącego wyjątku skojarzonego ze zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="e8ae7-110">An array of strings, each of which specifies a parameter for the current exception associated with the event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="e8ae7-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="e8ae7-111">Requirements</span></span>  
 <span data-ttu-id="e8ae7-112">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e8ae7-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e8ae7-113">**Nagłówek:** MSCorEE. idl</span><span class="sxs-lookup"><span data-stu-id="e8ae7-113">**Header:** MSCorEE.idl</span></span>  
  
 <span data-ttu-id="e8ae7-114">**.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e8ae7-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8ae7-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8ae7-115">See also</span></span>

- [<span data-ttu-id="e8ae7-116">Hosting, struktury</span><span class="sxs-lookup"><span data-stu-id="e8ae7-116">Hosting Structures</span></span>](hosting-structures.md)
