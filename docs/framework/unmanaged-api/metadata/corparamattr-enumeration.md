---
title: CorParamAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorParamAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorParamAttr
helpviewer_keywords:
- CorParamAttr enumeration [.NET Framework metadata]
ms.assetid: a7ff90ad-dad8-48e8-917d-4aa9a118cbc8
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 97f62b082db11a5f0bb930e33cb47acef76e7a04
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59092061"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="89aa6-102">CorParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="89aa6-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="89aa6-103">Zawiera wartości, które opisują metadane parametrem metody.</span><span class="sxs-lookup"><span data-stu-id="89aa6-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="89aa6-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="89aa6-104">Syntax</span></span>  
  
```  
typedef enum CorParamAttr {  
  
    pdIn                        =   0x0001,  
    pdOut                       =   0x0002,  
    pdOptional                  =   0x0010,  
  
    pdReservedMask              =   0xf000,  
    pdHasDefault                =   0x1000,  
    pdHasFieldMarshal           =   0x2000,  
  
    pdUnused                    =   0xcfe0  
  
} CorParamAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="89aa6-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="89aa6-105">Members</span></span>  
  
|<span data-ttu-id="89aa6-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="89aa6-106">Member</span></span>|<span data-ttu-id="89aa6-107">Opis</span><span class="sxs-lookup"><span data-stu-id="89aa6-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="89aa6-108">Określa, że parametr jest przekazywany do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="89aa6-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="89aa6-109">Określa, że parametr jest przekazywany z metody zwrotu.</span><span class="sxs-lookup"><span data-stu-id="89aa6-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="89aa6-110">Określa, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="89aa6-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="89aa6-111">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="89aa6-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="89aa6-112">Określa, że parametr ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="89aa6-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="89aa6-113">Określa, że parametr ma organizowanie informacji.</span><span class="sxs-lookup"><span data-stu-id="89aa6-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="89aa6-114">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="89aa6-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="89aa6-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="89aa6-115">Requirements</span></span>  
 <span data-ttu-id="89aa6-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="89aa6-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="89aa6-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="89aa6-117">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="89aa6-118">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="89aa6-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="89aa6-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="89aa6-119">See also</span></span>

- [<span data-ttu-id="89aa6-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="89aa6-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
