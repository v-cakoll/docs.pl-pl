---
title: "CorArgType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorArgType
api_location: mscoree.dll
api_type: COM
f1_keywords: CorArgType
helpviewer_keywords: CorArgType enumeration [.NET Framework metadata]
ms.assetid: 3c1cb268-57a0-4664-91c7-f6908ff29e32
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 22034b575dee2840cb89b949f5c663df27cefc4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="corargtype-enumeration"></a><span data-ttu-id="fd5af-102">CorArgType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="fd5af-102">CorArgType Enumeration</span></span>
<span data-ttu-id="fd5af-103">Zawiera wartości, które opisują natywny typ dojścia środowiska wykonawczego.</span><span class="sxs-lookup"><span data-stu-id="fd5af-103">Contains values that describe the native type of a runtime handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fd5af-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="fd5af-104">Syntax</span></span>  
  
```  
typedef enum CorArgType {  
  
    IMAGE_CEE_CS_END        = 0x0,  
    IMAGE_CEE_CS_VOID       = 0x1,  
    IMAGE_CEE_CS_I4         = 0x2,  
    IMAGE_CEE_CS_I8         = 0x3,  
    IMAGE_CEE_CS_R4         = 0x4,  
    IMAGE_CEE_CS_R8         = 0x5,  
    IMAGE_CEE_CS_PTR        = 0x6,  
    IMAGE_CEE_CS_OBJECT     = 0x7,  
    IMAGE_CEE_CS_STRUCT4    = 0x8,  
    IMAGE_CEE_CS_STRUCT32   = 0x9,  
    IMAGE_CEE_CS_BYVALUE    = 0xA  
  
} CorArgType;  
```  
  
## <a name="requirements"></a><span data-ttu-id="fd5af-105">Wymagania</span><span class="sxs-lookup"><span data-stu-id="fd5af-105">Requirements</span></span>  
 <span data-ttu-id="fd5af-106">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fd5af-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fd5af-107">**Nagłówek:** CorHdr.h</span><span class="sxs-lookup"><span data-stu-id="fd5af-107">**Header:** CorHdr.h</span></span>  
  
 <span data-ttu-id="fd5af-108">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fd5af-108">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fd5af-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fd5af-109">See Also</span></span>  
 [<span data-ttu-id="fd5af-110">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="fd5af-110">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
