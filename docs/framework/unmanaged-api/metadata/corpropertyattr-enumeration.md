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
ms.openlocfilehash: f1a0fff266e964b506b2dc7c4030caa54abaa5ed
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59171824"
---
# <a name="corpropertyattr-enumeration"></a><span data-ttu-id="a1f03-102">CorPropertyAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a1f03-102">CorPropertyAttr Enumeration</span></span>
<span data-ttu-id="a1f03-103">Zawiera wartości, które opisują metadane właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1f03-103">Contains values that describe the metadata of a property.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1f03-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a1f03-104">Syntax</span></span>  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="a1f03-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a1f03-105">Members</span></span>  
  
|<span data-ttu-id="a1f03-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a1f03-106">Member</span></span>|<span data-ttu-id="a1f03-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a1f03-107">Description</span></span>|  
|------------|-----------------|  
|`prSpecialName`|<span data-ttu-id="a1f03-108">Określa, czy właściwość jest specjalne i że jego nazwę w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="a1f03-108">Specifies that the property is special, and that its name describes how.</span></span>|  
|`prReservedMask`|<span data-ttu-id="a1f03-109">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a1f03-109">Reserved for internal use by the common language runtime.</span></span>|  
|`prRTSpecialName`|<span data-ttu-id="a1f03-110">Określa, że typowe metadanych środowiska wykonawczego języka wewnętrznych interfejsach API należy sprawdzać kodowanie nazwy właściwości.</span><span class="sxs-lookup"><span data-stu-id="a1f03-110">Specifies that the common language runtime metadata internal APIs should check the encoding of the property name.</span></span>|  
|`prHasDefault`|<span data-ttu-id="a1f03-111">Określa, że właściwość ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="a1f03-111">Specifies that the property has a default value.</span></span>|  
|`prUnused`|<span data-ttu-id="a1f03-112">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="a1f03-112">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a1f03-113">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a1f03-113">Requirements</span></span>  
 <span data-ttu-id="a1f03-114">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1f03-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1f03-115">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="a1f03-115">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="a1f03-116">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="a1f03-116">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a1f03-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1f03-117">See also</span></span>

- [<span data-ttu-id="a1f03-118">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a1f03-118">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
