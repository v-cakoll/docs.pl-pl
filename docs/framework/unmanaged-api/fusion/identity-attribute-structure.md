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
ms.openlocfilehash: cb970d31fb5158adc7dbcbb7cc0175cc91c83c8c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698047"
---
# <a name="identityattribute-structure"></a><span data-ttu-id="ec4c0-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="ec4c0-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="ec4c0-103">Zawiera informacje o atrybutach metadane dotyczące [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-103">Contains metadata attribute information about an [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ec4c0-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ec4c0-104">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="ec4c0-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ec4c0-105">Members</span></span>  
  
|<span data-ttu-id="ec4c0-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ec4c0-106">Member</span></span>|<span data-ttu-id="ec4c0-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ec4c0-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="ec4c0-108">Wskaźnik do ciągu zakończonego znakiem null, zawierającą przestrzeń nazw atrybut jest.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="ec4c0-109">Wskaźnik do ciągu zakończonego znakiem null, zawierający nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="ec4c0-110">Wskaźnik do ciągu zakończonego znakiem null, zawierający wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ec4c0-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ec4c0-111">Remarks</span></span>  
 <span data-ttu-id="ec4c0-112">`IDENTITY_ATTRIBUTE` Struktura zawiera trzy wskaźnikami do ciągów znaków zakończony znakiem null.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="ec4c0-113">Te trzy ciągi opisują jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="ec4c0-114">Wystąpienie `IDENTITY_ATTRIBUTE` struktury jest skojarzony z wystąpieniem [identity_attribute_blob —](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) struktury.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="ec4c0-115">`IDENTITY_ATTRIBUTE` Struktura zawiera rzeczywiste ciągów i odpowiedni `IDENTITY_ATTRIBUTE_BLOB` struktura zawiera listę przesunięć na trzy ciągi na liście `IDENTITY_ATTRIBUTE` struktury.</span><span class="sxs-lookup"><span data-stu-id="ec4c0-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="ec4c0-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ec4c0-116">Requirements</span></span>  
 <span data-ttu-id="ec4c0-117">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ec4c0-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ec4c0-118">**Nagłówek:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="ec4c0-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="ec4c0-119">**Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ec4c0-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec4c0-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ec4c0-120">See also</span></span>

- [<span data-ttu-id="ec4c0-121">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="ec4c0-121">IDefinitionIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md)
- [<span data-ttu-id="ec4c0-122">IDENTITY_ATTRIBUTE_BLOB, struktura</span><span class="sxs-lookup"><span data-stu-id="ec4c0-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-blob-structure.md)
- [<span data-ttu-id="ec4c0-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="ec4c0-123">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
