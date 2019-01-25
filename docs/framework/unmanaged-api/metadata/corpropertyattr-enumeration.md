---
title: CorPropertyAttr — Wyliczenie
ms.date: 03/30/2017
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 713913fa046fc1bef12b8849ac82e4399a8dc534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577587"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="cd729-102">CorPropertyAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="cd729-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="cd729-103">Zawiera wartości, które opisują metadane właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd729-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cd729-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="cd729-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="cd729-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="cd729-105">Members</span></span>  
  
|<span data-ttu-id="cd729-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="cd729-106">Member</span></span>|<span data-ttu-id="cd729-107">Opis</span><span class="sxs-lookup"><span data-stu-id="cd729-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="cd729-108">Określa, czy właściwość jest specjalne i że jego nazwę w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="cd729-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="cd729-109">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="cd729-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="cd729-110">Określa, że typowe metadanych środowiska wykonawczego języka wewnętrznych interfejsach API należy sprawdzać kodowanie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="cd729-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="cd729-111">Określa, że właściwość ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="cd729-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="cd729-112">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="cd729-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="cd729-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="cd729-113">Requirements</span></span>  
 <span data-ttu-id="cd729-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cd729-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cd729-115">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="cd729-115">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="cd729-116">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cd729-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cd729-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cd729-117">See also</span></span>
- [<span data-ttu-id="cd729-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="cd729-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
