---
title: CorEventAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorEventAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorEventAttr
helpviewer_keywords:
- CorEventAttr enumeration [.NET Framework metadata]
ms.assetid: dc2b3281-3820-487e-930d-350b66dc6417
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a1a50c15071ea1e696e508c779309225c7e7bfa2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097824"
---
# <a name="coreventattr-enumeration"></a><span data-ttu-id="410ed-102">CorEventAttr — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="410ed-102">CorEventAttr Enumeration</span></span>
<span data-ttu-id="410ed-103">Zawiera wartości, które opisują metadane zdarzenie.</span><span class="sxs-lookup"><span data-stu-id="410ed-103">Contains values that describe the metadata of an event.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="410ed-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="410ed-104">Syntax</span></span>  
  
```  
typedef enum CorEventAttr {  
  
    evSpecialName           =   0x0200,  
  
    evReservedMask          =   0x0400,  
    evRTSpecialName         =   0x0400,  
  
} CorEventAttr;  
```  
  
## <a name="members"></a><span data-ttu-id="410ed-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="410ed-105">Members</span></span>  
  
|<span data-ttu-id="410ed-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="410ed-106">Member</span></span>|<span data-ttu-id="410ed-107">Opis</span><span class="sxs-lookup"><span data-stu-id="410ed-107">Description</span></span>|  
|------------|-----------------|  
|`evSpecialName`|<span data-ttu-id="410ed-108">Określa, czy zdarzenie jest specjalne i że jego nazwę w tym artykule opisano sposób.</span><span class="sxs-lookup"><span data-stu-id="410ed-108">Specifies that the event is special, and that its name describes how.</span></span>|  
|`evReservedMask`|<span data-ttu-id="410ed-109">Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="410ed-109">Reserved for internal use by the common language runtime.</span></span>|  
|`evRTSpecialName`|<span data-ttu-id="410ed-110">Określa, że środowisko uruchomieniowe języka wspólnego powinien sprawdzać, kodowanie Nazwa zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="410ed-110">Specifies that the common language runtime should check the encoding of the event name.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="410ed-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="410ed-111">Requirements</span></span>  
 <span data-ttu-id="410ed-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="410ed-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="410ed-113">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="410ed-113">**Header:** CorHdr.h</span></span>  
  
 **<span data-ttu-id="410ed-114">Wersje programu .NET framework:</span><span class="sxs-lookup"><span data-stu-id="410ed-114">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="410ed-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="410ed-115">See also</span></span>

- [<span data-ttu-id="410ed-116">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="410ed-116">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
