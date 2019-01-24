---
title: CorThreadSafetyOptions — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorThreadSafetyOptions
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorThreadSafetyOptions
helpviewer_keywords:
- CorThreadSafetyOptions enumeration [.NET Framework metadata]
ms.assetid: dae07d9b-df51-488c-b17e-52d6e48217bd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b460c2c4b0d38ec46ee9d7341de9b320a2ecaa7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54594645"
---
# <a name="corthreadsafetyoptions-enumeration"></a><span data-ttu-id="d882f-102">CorThreadSafetyOptions — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="d882f-102">CorThreadSafetyOptions Enumeration</span></span>
<span data-ttu-id="d882f-103">Określa flagi, aby wybrać opcje bezpieczeństwo wątkowe.</span><span class="sxs-lookup"><span data-stu-id="d882f-103">Specifies flags to select options for thread safety.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d882f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="d882f-104">Syntax</span></span>  
  
```  
typedef enum CorThreadSafetyOptions {  
    MDThreadSafetyDefault       = 0x00000000,  
    MDThreadSafetyOff           = 0x00000000,  
    MDThreadSafetyOn            = 0x00000001,  
} CorThreadSafetyOptions;  
```  
  
## <a name="members"></a><span data-ttu-id="d882f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="d882f-105">Members</span></span>  
  
|<span data-ttu-id="d882f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="d882f-106">Member</span></span>|<span data-ttu-id="d882f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="d882f-107">Description</span></span>|  
|------------|-----------------|  
|`MDThreadSatetyDefault`|<span data-ttu-id="d882f-108">Wartość domyślna.</span><span class="sxs-lookup"><span data-stu-id="d882f-108">Default value.</span></span> <span data-ttu-id="d882f-109">Taki sam jak `MDThreadSatetyOff`.</span><span class="sxs-lookup"><span data-stu-id="d882f-109">Same as `MDThreadSatetyOff`.</span></span>|  
|`MDThreadSatetyOff`|<span data-ttu-id="d882f-110">Wskazuje, nie można ustawić czytnika/blokadę.</span><span class="sxs-lookup"><span data-stu-id="d882f-110">Indicates that a reader/writer lock cannot be set.</span></span>|  
|`MDThreadSatetyOn`|<span data-ttu-id="d882f-111">Wskazuje, że czytnik/blokadę można ustawić.</span><span class="sxs-lookup"><span data-stu-id="d882f-111">Indicates that a reader/writer lock can be set.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d882f-112">Wymagania</span><span class="sxs-lookup"><span data-stu-id="d882f-112">Requirements</span></span>  
 <span data-ttu-id="d882f-113">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d882f-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d882f-114">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="d882f-114">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="d882f-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d882f-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d882f-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d882f-116">See also</span></span>
- [<span data-ttu-id="d882f-117">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="d882f-117">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
