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
ms.openlocfilehash: 7d07c6de47038d5c52d76ad8ca8e0a5684551d59
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491470"
---
# <a name="corparamattr-enumeration"></a><span data-ttu-id="4ab9f-102">CorParamAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="4ab9f-102">CorParamAttr Enumeration</span></span>
<span data-ttu-id="4ab9f-103">Zawiera wartości, które opisują metadane parametrem metody.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-103">Contains values that describe the metadata of a method parameter.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ab9f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="4ab9f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="4ab9f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="4ab9f-105">Members</span></span>  
  
|<span data-ttu-id="4ab9f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="4ab9f-106">Member</span></span>|<span data-ttu-id="4ab9f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="4ab9f-107">Description</span></span>|  
|------------|-----------------|  
|`pdIn`|<span data-ttu-id="4ab9f-108">Określa, że parametr jest przekazywany do wywołania metody.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-108">Specifies that the parameter is passed into the method call.</span></span>|  
|`pdOut`|<span data-ttu-id="4ab9f-109">Określa, że parametr jest przekazywany z metody zwrotu.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-109">Specifies that the parameter is passed from the method return.</span></span>|  
|`pdOptional`|<span data-ttu-id="4ab9f-110">Określa, że parametr jest opcjonalny.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-110">Specifies that the parameter is optional.</span></span>|  
|`pdReservedMask`|<span data-ttu-id="4ab9f-111">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-111">Reserved for internal use by the common language runtime.</span></span>|  
|`pdHasDefault`|<span data-ttu-id="4ab9f-112">Określa, że parametr ma wartość domyślną.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-112">Specifies that the parameter has a default value.</span></span>|  
|`pdHasFieldMarshal`|<span data-ttu-id="4ab9f-113">Określa, że parametr ma organizowanie informacji.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-113">Specifies that the parameter has marshaling information.</span></span>|  
|`pdUnused`|<span data-ttu-id="4ab9f-114">Nieużywane.</span><span class="sxs-lookup"><span data-stu-id="4ab9f-114">Unused.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="4ab9f-115">Wymagania</span><span class="sxs-lookup"><span data-stu-id="4ab9f-115">Requirements</span></span>  
 <span data-ttu-id="4ab9f-116">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4ab9f-116">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4ab9f-117">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="4ab9f-117">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="4ab9f-118">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4ab9f-118">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ab9f-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4ab9f-119">See also</span></span>
- [<span data-ttu-id="4ab9f-120">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="4ab9f-120">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
