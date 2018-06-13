---
title: IDENTITY_ATTRIBUTE — Struktura
ms.date: 03/30/2017
api_name:
- IDENTITY_ATTRIBUTE
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE
helpviewer_keywords:
- IDENTITY_ATTRIBUTE structure [.NET Framework fusion]
ms.assetid: 1ee7c434-9681-4fa8-badd-652cb1a9742b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f716ff35ae0cd3d2a53c55756b8957e54fa355c6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33431538"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="998b4-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="998b4-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="998b4-103">Zawiera informacje o atrybutach metadane dotyczące [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="998b4-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="998b4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="998b4-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="998b4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="998b4-105">Members</span></span>  
  
|<span data-ttu-id="998b4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="998b4-106">Member</span></span>|<span data-ttu-id="998b4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="998b4-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="998b4-108">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera przestrzeń nazw atrybutu jest w.</span><span class="sxs-lookup"><span data-stu-id="998b4-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="998b4-109">Wskaźnik do ciąg znaków zakończony znakiem null, który zawiera nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="998b4-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="998b4-110">Wskaźnik na ciąg znaków zakończony znakiem null zawierającym wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="998b4-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="998b4-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="998b4-111">Remarks</span></span>  
 <span data-ttu-id="998b4-112">`IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźniki do ciągów znaków zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="998b4-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="998b4-113">Te trzy ciągi opisano jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="998b4-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="998b4-114">Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="998b4-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="998b4-115">`IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiadający mu `IDENTITY_ATTRIBUTE_BLOB` przesunięcia na trzy ciągi, na liście wymieniono struktury `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="998b4-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="998b4-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="998b4-116">Requirements</span></span>  
 <span data-ttu-id="998b4-117">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="998b4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="998b4-118">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="998b4-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="998b4-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="998b4-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="998b4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="998b4-120">See Also</span></span>  
 [<span data-ttu-id="998b4-121">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="998b4-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)  
 [<span data-ttu-id="998b4-122">IDENTITY_ATTRIBUTE_BLOB, struktura</span><span class="sxs-lookup"><span data-stu-id="998b4-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)  
 [<span data-ttu-id="998b4-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="998b4-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
