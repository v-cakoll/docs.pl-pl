---
title: "CeeSectionRelocExtra — Unia"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CeeSectionRelocExtra Union
api_location: mscoree.dll
api_type: COM
f1_keywords: CeeSectionRelocExtra
helpviewer_keywords: CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c5b584ced996b31be6656082af3f64a19b1f223c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="3bdb8-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="3bdb8-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="3bdb8-103">Reprezentuje adres używany przez przesunięcie [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejs może przenosić sekcji.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3bdb8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3bdb8-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="3bdb8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3bdb8-105">Members</span></span>  
  
|<span data-ttu-id="3bdb8-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3bdb8-106">Member</span></span>|<span data-ttu-id="3bdb8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3bdb8-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="3bdb8-108">Korekta górny adres dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="3bdb8-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3bdb8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3bdb8-109">Requirements</span></span>  
 <span data-ttu-id="3bdb8-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3bdb8-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3bdb8-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3bdb8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3bdb8-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3bdb8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3bdb8-113">**Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3bdb8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3bdb8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3bdb8-114">See Also</span></span>  
 [<span data-ttu-id="3bdb8-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="3bdb8-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
