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
ms.openlocfilehash: d11fefe220fdb00457cc48a6cd166673350be049
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006037"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="3d7a8-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="3d7a8-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="3d7a8-103">Reprezentuje przesunięcie adresu, które jest używane przez interfejs [ICeeGen](iceegen-interface.md) , aby przenieść sekcję.</span><span class="sxs-lookup"><span data-stu-id="3d7a8-103">Represents an address offset that is used by the [ICeeGen](iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3d7a8-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3d7a8-104">Syntax</span></span>  
  
```cpp  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="3d7a8-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3d7a8-105">Members</span></span>  
  
|<span data-ttu-id="3d7a8-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3d7a8-106">Member</span></span>|<span data-ttu-id="3d7a8-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3d7a8-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="3d7a8-108">Górne dopasowanie adresu dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="3d7a8-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3d7a8-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3d7a8-109">Requirements</span></span>  
 <span data-ttu-id="3d7a8-110">**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3d7a8-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3d7a8-111">**Nagłówek:** Cor. h</span><span class="sxs-lookup"><span data-stu-id="3d7a8-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3d7a8-112">**Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="3d7a8-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3d7a8-113">**.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3d7a8-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3d7a8-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3d7a8-114">See also</span></span>

- [<span data-ttu-id="3d7a8-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="3d7a8-115">Metadata Unions</span></span>](metadata-unions.md)
