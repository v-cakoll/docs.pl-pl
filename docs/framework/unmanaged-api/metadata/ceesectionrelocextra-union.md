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
ms.openlocfilehash: c7634ec801a30aa7ba07954c1df0c3d37ec279eb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440304"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="3f1fc-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="3f1fc-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="3f1fc-103">Reprezentuje adres używany przez przesunięcie [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejs może przenosić sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f1fc-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3f1fc-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3f1fc-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="3f1fc-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3f1fc-105">Members</span></span>  
  
|<span data-ttu-id="3f1fc-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="3f1fc-106">Member</span></span>|<span data-ttu-id="3f1fc-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3f1fc-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="3f1fc-108">Korekta górny adres dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="3f1fc-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3f1fc-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3f1fc-109">Requirements</span></span>  
 <span data-ttu-id="3f1fc-110">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3f1fc-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3f1fc-111">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3f1fc-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3f1fc-112">**Biblioteka:** uwzględnione jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3f1fc-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3f1fc-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3f1fc-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f1fc-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f1fc-114">See Also</span></span>  
 [<span data-ttu-id="3f1fc-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="3f1fc-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
