---
title: CeeSectionRelocExtra — Unia
ms.date: 03/30/2017
api_name:
- CeeSectionRelocExtra Union
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocExtra
helpviewer_keywords:
- CeeSectionRelocExtra union [.NET Framework metadata]
ms.assetid: d9568cf6-7f98-4cd6-ab36-0a2bd509afcc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8a78a4b82d0b2064c90c938a8614b0c7594f7856
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182276"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="9a26f-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="9a26f-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="9a26f-103">Reprezentuje Przesunięcie adresu, który jest używany przez [iceegen —](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejsu przenosić sekcji.</span><span class="sxs-lookup"><span data-stu-id="9a26f-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a26f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="9a26f-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="9a26f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="9a26f-105">Members</span></span>  
  
|<span data-ttu-id="9a26f-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="9a26f-106">Member</span></span>|<span data-ttu-id="9a26f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="9a26f-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="9a26f-108">Korekta górny adres dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="9a26f-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="9a26f-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="9a26f-109">Requirements</span></span>  
 <span data-ttu-id="9a26f-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9a26f-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9a26f-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="9a26f-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="9a26f-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="9a26f-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="9a26f-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9a26f-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a26f-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a26f-114">See also</span></span>

- [<span data-ttu-id="9a26f-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="9a26f-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
