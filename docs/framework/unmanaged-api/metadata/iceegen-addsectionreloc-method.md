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
ms.openlocfilehash: c281d03c6e3774938cfa6e4b4b3a541738b38489
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="03baa-102">ICeeGen::AddSectionReloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="03baa-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="03baa-103">Dodaje instrukcję .reloc do ścieżki bazowej kodu.</span><span class="sxs-lookup"><span data-stu-id="03baa-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="03baa-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="03baa-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03baa-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="03baa-105">Syntax</span></span>  
  
```  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="03baa-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="03baa-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="03baa-107">[in] Sekcji kodu w pamięci, do której ma zostać dodany instrukcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="03baa-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="03baa-108">[in] Przesunięcie sekcji.</span><span class="sxs-lookup"><span data-stu-id="03baa-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="03baa-109">[in] Sekcja, do którego `offset` odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="03baa-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="03baa-110">[in] Jeden z [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) wartości i wskazujący rodzaj .reloc instrukcji, aby dodać.</span><span class="sxs-lookup"><span data-stu-id="03baa-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="03baa-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="03baa-111">Requirements</span></span>  
 <span data-ttu-id="03baa-112">**Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="03baa-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="03baa-113">**Nagłówek:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="03baa-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="03baa-114">**Biblioteka:** używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="03baa-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="03baa-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="03baa-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03baa-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03baa-116">See Also</span></span>  
 [<span data-ttu-id="03baa-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="03baa-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
