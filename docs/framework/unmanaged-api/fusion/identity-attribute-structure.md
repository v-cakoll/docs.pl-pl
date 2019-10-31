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
ms.openlocfilehash: 8b7edf1cc642228c4a79c855b51727264f31741c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73107987"
---
# <a name="identity_attribute-structure"></a><span data-ttu-id="50504-102">IDENTITY_ATTRIBUTE — Struktura</span><span class="sxs-lookup"><span data-stu-id="50504-102">IDENTITY_ATTRIBUTE Structure</span></span>
<span data-ttu-id="50504-103">Zawiera informacje o atrybucie metadanych dotyczące wystąpienia [IDefinitionIdentity —](idefinitionidentity-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="50504-103">Contains metadata attribute information about an [IDefinitionIdentity](idefinitionidentity-interface.md) instance.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="50504-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="50504-104">Syntax</span></span>  
  
```cpp  
typedef struct _IDENTITY_ATTRIBUTE {  
    LPCWSTR  pszNamespace;  
    LPCWSTR  pszName;  
    LPCWSTR  pszValue;  
} IDENTITY_ATTRIBUTE;  
```  
  
## <a name="members"></a><span data-ttu-id="50504-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="50504-105">Members</span></span>  
  
|<span data-ttu-id="50504-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="50504-106">Member</span></span>|<span data-ttu-id="50504-107">Opis</span><span class="sxs-lookup"><span data-stu-id="50504-107">Description</span></span>|  
|------------|-----------------|  
|`pszNamespace`|<span data-ttu-id="50504-108">Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera przestrzeń nazw, w której znajduje się atrybut.</span><span class="sxs-lookup"><span data-stu-id="50504-108">A pointer to a null-terminated character string that contains the namespace the attribute is in.</span></span>|  
|`pszName`|<span data-ttu-id="50504-109">Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera nazwę atrybutu.</span><span class="sxs-lookup"><span data-stu-id="50504-109">A pointer to a null-terminated character string that contains the name of the attribute.</span></span>|  
|`pszValue`|<span data-ttu-id="50504-110">Wskaźnik do ciągu znaków zakończonych znakiem null, który zawiera wartość atrybutu.</span><span class="sxs-lookup"><span data-stu-id="50504-110">A pointer to a null-terminated character string that contains the value of the attribute.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="50504-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50504-111">Remarks</span></span>  
 <span data-ttu-id="50504-112">Struktura `IDENTITY_ATTRIBUTE` zawiera trzy wskaźniki do ciągów znaków zakończonych znakiem null.</span><span class="sxs-lookup"><span data-stu-id="50504-112">The `IDENTITY_ATTRIBUTE` structure contains three pointers to null-terminated character strings.</span></span> <span data-ttu-id="50504-113">Te trzy ciągi opisują jeden atrybut.</span><span class="sxs-lookup"><span data-stu-id="50504-113">These three strings describe one attribute.</span></span>  
  
 <span data-ttu-id="50504-114">Wystąpienie struktury `IDENTITY_ATTRIBUTE` jest skojarzone z wystąpieniem struktury [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="50504-114">An instance of an `IDENTITY_ATTRIBUTE` structure is associated with an instance of an [IDENTITY_ATTRIBUTE_BLOB](identity-attribute-blob-structure.md) structure.</span></span> <span data-ttu-id="50504-115">Struktura `IDENTITY_ATTRIBUTE` zawiera rzeczywiste ciągi, a odpowiednia struktura `IDENTITY_ATTRIBUTE_BLOB` wyświetla przesunięcia na trzy ciągi wymienione w strukturze `IDENTITY_ATTRIBUTE`.</span><span class="sxs-lookup"><span data-stu-id="50504-115">The `IDENTITY_ATTRIBUTE` structure contains the actual strings, and the corresponding `IDENTITY_ATTRIBUTE_BLOB` structure lists the offsets to the three strings listed in the `IDENTITY_ATTRIBUTE` structure.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="50504-116">Wymagania</span><span class="sxs-lookup"><span data-stu-id="50504-116">Requirements</span></span>  
 <span data-ttu-id="50504-117">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="50504-117">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="50504-118">**Nagłówek:** Izolacja. h</span><span class="sxs-lookup"><span data-stu-id="50504-118">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="50504-119">**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="50504-119">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="50504-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="50504-120">See also</span></span>

- [<span data-ttu-id="50504-121">IDefinitionIdentity, interfejs</span><span class="sxs-lookup"><span data-stu-id="50504-121">IDefinitionIdentity Interface</span></span>](idefinitionidentity-interface.md)
- [<span data-ttu-id="50504-122">IDENTITY_ATTRIBUTE_BLOB, struktura</span><span class="sxs-lookup"><span data-stu-id="50504-122">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>](identity-attribute-blob-structure.md)
- [<span data-ttu-id="50504-123">Łączenie — struktury</span><span class="sxs-lookup"><span data-stu-id="50504-123">Fusion Structures</span></span>](fusion-structures.md)
