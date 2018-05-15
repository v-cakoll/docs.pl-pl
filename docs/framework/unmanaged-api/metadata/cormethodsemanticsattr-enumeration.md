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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: de467c98dfa7ad3eac69502f2afe311b301e1ec5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="cormethodsemanticsattr-enumeration"></a><span data-ttu-id="69963-102">CorMethodSemanticsAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="69963-102">CorMethodSemanticsAttr Enumeration</span></span>
<span data-ttu-id="69963-103">Zawiera wartości, które opisują relację między metody i skojarzonej właściwości lub zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="69963-103">Contains values that describe the relationship between a method and an associated property or event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69963-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="69963-104">Syntax</span></span>  
  
```  
typedef enum CorMethodSemanticsAttr {  
  
    msSetter    =   0x0001,  
    msGetter    =   0x0002,  
    msOther     =   0x0004,  
    msAddOn     =   0x0008,  
    msRemoveOn  =   0x0010,  
    msFire      =   0x0020,  
  
} CorMethodSemanticsAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="69963-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="69963-105">Members</span></span>  
  
|<span data-ttu-id="69963-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="69963-106">Member</span></span>|<span data-ttu-id="69963-107">Opis</span><span class="sxs-lookup"><span data-stu-id="69963-107">Description</span></span>|  
|------------|-----------------|  
|`msSetter`|<span data-ttu-id="69963-108">Określa, że metoda jest `set` metody dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="69963-108">Specifies that the method is a `set` accessor for a property.</span></span>|  
|`msGetter`|<span data-ttu-id="69963-109">Określa, że metoda jest `get` metody dostępu właściwości.</span><span class="sxs-lookup"><span data-stu-id="69963-109">Specifies that the method is a `get` accessor for a property.</span></span>|  
|`msOther`|<span data-ttu-id="69963-110">Określa, że metoda ma relacji z właściwości lub zdarzenia innych niż te, zdefiniowane w tym miejscu.</span><span class="sxs-lookup"><span data-stu-id="69963-110">Specifies that the method has a relationship to a property or an event other than those defined here.</span></span>|  
|`msAddOn`|<span data-ttu-id="69963-111">Określa, że metoda dodaje metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69963-111">Specifies that the method adds handler methods for an event.</span></span>|  
|`msRemoveOn`|<span data-ttu-id="69963-112">Określa, że metoda usuwa metody obsługi zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="69963-112">Specifies that the method removes handler methods for an event.</span></span>|  
|`msFire`|<span data-ttu-id="69963-113">Określa, że metoda wywołuje zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="69963-113">Specifies that the method raises an event.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="69963-114">Wymagania</span><span class="sxs-lookup"><span data-stu-id="69963-114">Requirements</span></span>  
 <span data-ttu-id="69963-115">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="69963-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="69963-116">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="69963-116">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="69963-117">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="69963-117">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="69963-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="69963-118">See Also</span></span>  
 [<span data-ttu-id="69963-119">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="69963-119">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
