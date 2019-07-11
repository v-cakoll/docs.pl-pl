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
ms.openlocfilehash: da3b83191ce1acdf40e27c5ee1d843a1fb4a54f8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67750680"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="bb3be-102">ICeeGen::AddSectionReloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="bb3be-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="bb3be-103">Dodaje instrukcję .reloc do bazy kodu.</span><span class="sxs-lookup"><span data-stu-id="bb3be-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="bb3be-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="bb3be-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb3be-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="bb3be-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,   
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="bb3be-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="bb3be-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="bb3be-107">[in] Sekcja kodu w pamięci, do której chcesz dodać instrukcję .reloc.</span><span class="sxs-lookup"><span data-stu-id="bb3be-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="bb3be-108">[in] Przesunięcie sekcji.</span><span class="sxs-lookup"><span data-stu-id="bb3be-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="bb3be-109">[in] Sekcja, do którego `offset` odwołuje się.</span><span class="sxs-lookup"><span data-stu-id="bb3be-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="bb3be-110">[in] Jedną z [ceesectionreloctype —](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) wartości, wskazujący rodzaj instrukcji .reloc do dodania.</span><span class="sxs-lookup"><span data-stu-id="bb3be-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb3be-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="bb3be-111">Requirements</span></span>  
 <span data-ttu-id="bb3be-112">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb3be-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb3be-113">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="bb3be-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="bb3be-114">**Biblioteka:** Używany jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="bb3be-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="bb3be-115">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb3be-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb3be-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="bb3be-116">See also</span></span>

- [<span data-ttu-id="bb3be-117">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="bb3be-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
