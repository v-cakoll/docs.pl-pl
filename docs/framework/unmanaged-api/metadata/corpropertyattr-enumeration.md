---
title: "CorPropertyAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4470cd46653dd798718e5b3413dbc021a894138b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="661d5-102">CorPropertyAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="661d5-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="661d5-103">Zawiera wartości, które opisują metadane właściwości.</span><span class="sxs-lookup"><span data-stu-id="661d5-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="661d5-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="661d5-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="661d5-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="661d5-105">Members</span></span>  
  
|<span data-ttu-id="661d5-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="661d5-106">Member</span></span>|<span data-ttu-id="661d5-107">Opis</span><span class="sxs-lookup"><span data-stu-id="661d5-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="661d5-108">Określa, czy właściwość jest szczególna i że jego nazwa zawiera opis sposobu.</span><span class="sxs-lookup"><span data-stu-id="661d5-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="661d5-109">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="661d5-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="661d5-110">Określa, że typowe metadane środowiska wykonawczego języka wewnętrznych interfejsów API należy sprawdzać kodowanie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="661d5-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="661d5-111">Określa, że właściwość ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="661d5-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="661d5-112">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="661d5-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="661d5-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="661d5-113">Requirements</span></span>  
 <span data-ttu-id="661d5-114">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="661d5-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="661d5-115">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="661d5-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="661d5-116">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="661d5-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="661d5-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="661d5-117">See Also</span></span>  
 [<span data-ttu-id="661d5-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="661d5-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
