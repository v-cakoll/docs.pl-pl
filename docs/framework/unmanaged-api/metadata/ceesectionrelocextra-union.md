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
ms.openlocfilehash: 7becace679b62a635d8231c3d42213f247f44190
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444178"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="26db4-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="26db4-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="26db4-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span><span class="sxs-lookup"><span data-stu-id="26db4-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="26db4-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="26db4-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="26db4-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="26db4-105">Members</span></span>  
  
|<span data-ttu-id="26db4-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="26db4-106">Member</span></span>|<span data-ttu-id="26db4-107">Opis</span><span class="sxs-lookup"><span data-stu-id="26db4-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="26db4-108">The upper address adjustment for the section.</span><span class="sxs-lookup"><span data-stu-id="26db4-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="26db4-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="26db4-109">Requirements</span></span>  
 <span data-ttu-id="26db4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="26db4-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="26db4-111">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="26db4-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="26db4-112">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="26db4-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="26db4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="26db4-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="26db4-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="26db4-114">See also</span></span>

- [<span data-ttu-id="26db4-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="26db4-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
