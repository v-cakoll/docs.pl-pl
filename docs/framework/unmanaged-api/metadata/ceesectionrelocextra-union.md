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
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62043293"
---
# <a name="ceesectionrelocextra-union"></a><span data-ttu-id="660be-102">CeeSectionRelocExtra — Unia</span><span class="sxs-lookup"><span data-stu-id="660be-102">CeeSectionRelocExtra Union</span></span>
<span data-ttu-id="660be-103">Reprezentuje Przesunięcie adresu, który jest używany przez [iceegen —](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interfejsu przenosić sekcji.</span><span class="sxs-lookup"><span data-stu-id="660be-103">Represents an address offset that is used by the [ICeeGen](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md) interface to relocate a section.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="660be-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="660be-104">Syntax</span></span>  
  
```  
typedef union  {  
    USHORT highAdj;  
} CeeSectionRelocExtra;  
```  
  
## <a name="members"></a><span data-ttu-id="660be-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="660be-105">Members</span></span>  
  
|<span data-ttu-id="660be-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="660be-106">Member</span></span>|<span data-ttu-id="660be-107">Opis</span><span class="sxs-lookup"><span data-stu-id="660be-107">Description</span></span>|  
|------------|-----------------|  
|`highAdj`|<span data-ttu-id="660be-108">Korekta górny adres dla sekcji.</span><span class="sxs-lookup"><span data-stu-id="660be-108">The upper address adjustment for the section.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="660be-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="660be-109">Requirements</span></span>  
 <span data-ttu-id="660be-110">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="660be-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="660be-111">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="660be-111">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="660be-112">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="660be-112">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="660be-113">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="660be-113">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="660be-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="660be-114">See also</span></span>

- [<span data-ttu-id="660be-115">Unie metadanych</span><span class="sxs-lookup"><span data-stu-id="660be-115">Metadata Unions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-unions.md)
