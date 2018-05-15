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
ms.openlocfilehash: 6ba2103003e3976e51e82ad6b42315a881582f5a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="ab9d9-102">CorParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab9d9-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="ab9d9-103">Zawiera wartości, które opisują metadanych parametru metody.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab9d9-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab9d9-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="ab9d9-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ab9d9-105">Members</span></span>  
  
|<span data-ttu-id="ab9d9-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ab9d9-106">Member</span></span>|<span data-ttu-id="ab9d9-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ab9d9-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="ab9d9-108">Określa, że parametr jest przekazywany do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="ab9d9-109">Określa, że parametr jest przekazywany z metody zwracany.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="ab9d9-110">Określa, czy parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="ab9d9-111">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="ab9d9-112">Określa, że parametr ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="ab9d9-113">Określa, czy parametr zawiera informacje organizacyjne.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="ab9d9-114">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="ab9d9-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab9d9-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab9d9-115">Requirements</span></span>  
 <span data-ttu-id="ab9d9-116">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab9d9-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab9d9-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="ab9d9-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="ab9d9-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab9d9-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab9d9-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ab9d9-119">See Also</span></span>  
 [<span data-ttu-id="ab9d9-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ab9d9-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
