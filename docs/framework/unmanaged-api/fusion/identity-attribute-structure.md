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
ms.openlocfilehash: e26a90b6725d53774053293c04842b761da6ab12
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717678"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="1c819-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="1c819-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="1c819-103">Zawiera informacje o atrybutach metadane dotyczące [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="1c819-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c819-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="1c819-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="1c819-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="1c819-105">Members</span></span>  
  
|<span data-ttu-id="1c819-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="1c819-106">Member</span></span>|<span data-ttu-id="1c819-107">Opis</span><span class="sxs-lookup"><span data-stu-id="1c819-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="1c819-108">Wskaźnik do ciągu zakończonego znakiem null, zawierającą przestrzeń nazw atrybut jest.</span><span class="sxs-lookup"><span data-stu-id="1c819-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="1c819-109">Wskaźnik do ciągu zakończonego znakiem null, zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1c819-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="1c819-110">Wskaźnik do ciągu zakończonego znakiem null, zawierający wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="1c819-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c819-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1c819-111">Remarks</span></span>  
 <span data-ttu-id="1c819-112">`IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźnikami do ciągów znaków zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="1c819-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="1c819-113">Te trzy ciągi opisują jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="1c819-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="1c819-114">Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="1c819-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="1c819-115">`IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiedni `IDENTITY_ATTRIBUTE_BLOB` struktura zawiera listę przesunięć na trzy ciągi na liście `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="1c819-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1c819-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="1c819-116">Requirements</span></span>  
 <span data-ttu-id="1c819-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1c819-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1c819-118">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="1c819-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="1c819-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1c819-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1c819-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1c819-120">See also</span></span>
- [<span data-ttu-id="1c819-121">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="1c819-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="1c819-122">IDENTITY_ATTRIBUTE_BLOB, struktura</span><span class="sxs-lookup"><span data-stu-id="1c819-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="1c819-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="1c819-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
