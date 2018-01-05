---
title: "IDENTITY_ATTRIBUTE — Struktura"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IDENTITY_ATTRIBUTE
helpviewer_keywords: IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2c0d09bf4c24f977a490f946cbc35b2b3f53dfc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="identityattribute-structure"></a><span data-ttu-id="502dd-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="502dd-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="502dd-103">Zawiera informacje o atrybutach metadane dotyczące [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="502dd-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="502dd-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="502dd-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="502dd-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="502dd-105">Members</span></span>  
  
|<span data-ttu-id="502dd-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="502dd-106">Member</span></span>|<span data-ttu-id="502dd-107">Opis</span><span class="sxs-lookup"><span data-stu-id="502dd-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="502dd-108">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera przestrzeń nazw atrybutu jest w.</span><span class="sxs-lookup"><span data-stu-id="502dd-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="502dd-109">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="502dd-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="502dd-110">Wskaźnik na ciąg znaków zakończony znakiem null zawierającym wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="502dd-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="502dd-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="502dd-111">Remarks</span></span>  
 <span data-ttu-id="502dd-112">`IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźniki do ciągów znaków zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="502dd-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="502dd-113">Te trzy ciągi opisano jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="502dd-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="502dd-114">Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="502dd-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="502dd-115">`IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiadający mu `IDENTITY_ATTRIBUTE_BLOB` przesunięcia na trzy ciągi, na liście wymieniono struktury `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="502dd-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="502dd-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="502dd-116">Requirements</span></span>  
 <span data-ttu-id="502dd-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="502dd-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="502dd-118">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="502dd-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="502dd-119">**Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="502dd-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="502dd-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="502dd-120">See Also</span></span>  
 [<span data-ttu-id="502dd-121">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="502dd-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="502dd-122">IDENTITY_ATTRIBUTE_BLOB, struktura</span><span class="sxs-lookup"><span data-stu-id="502dd-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="502dd-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="502dd-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
