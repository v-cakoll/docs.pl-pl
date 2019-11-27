---
title: CorMethodSemanticsAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorMethodSemanticsAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorMethodSemanticsAttr
helpviewer_keywords:
- CorMethodSemanticsAttr enumeration [.NET Framework metadata]
ms.assetid: ca2af325-eb9d-4a91-90e4-267e45b98611
topic_type:
- apiref
ms.openlocfilehash: bab215a8221696a0e43e228278085fcef52a40e9
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74442826"
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="0d375-102">CorMethodSemanticsAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="0d375-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="0d375-103">Zawiera wartości opisujące relacje między metodą a skojarzoną właściwością lub zdarzeniem.</span><span class="sxs-lookup"><span data-stu-id="0d375-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d375-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="0d375-104">Syntax</span></span>  
  
```cpp  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="0d375-105">Members</span><span class="sxs-lookup"><span data-stu-id="0d375-105">Members</span></span>  
  
|<span data-ttu-id="0d375-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="0d375-106">Member</span></span>|<span data-ttu-id="0d375-107">Opis</span><span class="sxs-lookup"><span data-stu-id="0d375-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="0d375-108">Określa, że metoda jest metodą dostępu `set` dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d375-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="0d375-109">Określa, że metoda jest metodą dostępu `get` dla właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d375-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="0d375-110">Określa, że metoda ma relację z właściwością lub zdarzeniem innym niż zdefiniowane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="0d375-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="0d375-111">Określa, że Metoda dodaje metody obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0d375-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="0d375-112">Określa, że metoda usuwa metody obsługi dla zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="0d375-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="0d375-113">Określa, że metoda wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="0d375-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="0d375-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0d375-114">Requirements</span></span>  
 <span data-ttu-id="0d375-115">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0d375-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0d375-116">**Nagłówek:** CorHdr. h</span><span class="sxs-lookup"><span data-stu-id="0d375-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="0d375-117">**Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0d375-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d375-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d375-118">See also</span></span>

- [<span data-ttu-id="0d375-119">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="0d375-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
