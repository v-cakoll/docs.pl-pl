---
title: ICeeGen::AddSectionReloc — Metoda
ms.date: 03/30/2017
api_name:
- ICeeGen.AddSectionReloc
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICeeGen::AddSectionReloc
helpviewer_keywords:
- AddSectionReloc method [.NET Framework metadata]
- ICeeGen::AddSectionReloc method [.NET Framework metadata]
ms.assetid: b500a260-1d57-4953-95e1-c27063f7c8da
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a8e270f45300bd5f8c2e6cd87f9b84f31ec42320
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54722195"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="7c1ac-102">ICeeGen::AddSectionReloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="7c1ac-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="7c1ac-103">Dodaje instrukcję .reloc do bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="7c1ac-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7c1ac-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7c1ac-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7c1ac-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7c1ac-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="7c1ac-107">[in] Sekcja kodu w pamięci, do której chcesz dodać instrukcję .reloc.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="7c1ac-108">[in] Przesunięcie sekcji.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="7c1ac-109">[in] Sekcja, do którego `offset` odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="7c1ac-110">[in] Jedną z [ceesectionreloctype —](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) wartości, wskazujący rodzaj instrukcji .reloc do dodania.</span><span class="sxs-lookup"><span data-stu-id="7c1ac-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7c1ac-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7c1ac-111">Requirements</span></span>  
 <span data-ttu-id="7c1ac-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7c1ac-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7c1ac-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="7c1ac-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="7c1ac-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="7c1ac-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="7c1ac-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7c1ac-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7c1ac-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7c1ac-116">See also</span></span>
- [<span data-ttu-id="7c1ac-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="7c1ac-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
