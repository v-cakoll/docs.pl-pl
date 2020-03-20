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
ms.openlocfilehash: 129750644962cee3206b9e38cbeaa77d38dddd71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176113"
---
# <a name="iceegenaddsectionreloc-method"></a><span data-ttu-id="2b7ea-102">ICeeGen::AddSectionReloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="2b7ea-102">ICeeGen::AddSectionReloc Method</span></span>
<span data-ttu-id="2b7ea-103">Dodaje instrukcję .reloc do podstawy kodu.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-103">Adds a .reloc instruction to the code base.</span></span>  
  
 <span data-ttu-id="2b7ea-104">Ta metoda jest przestarzała i nie powinna być używana.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-104">This method is obsolete and should not be used.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b7ea-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="2b7ea-105">Syntax</span></span>  
  
```cpp  
HRESULT AddSectionReloc (  
   [in] HCEESECTION            section,  
   [in] ULONG                  offset,  
   [in] HCEESECTION            relativeTo,
   [in] CeeSectionRelocType    relocType  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2b7ea-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="2b7ea-106">Parameters</span></span>  
 `section`  
 <span data-ttu-id="2b7ea-107">[w] Sekcja kodu w pamięci, do której należy dodać instrukcję .reloc.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-107">[in] The section of in-memory code to which to add a .reloc instruction.</span></span>  
  
 `offset`  
 <span data-ttu-id="2b7ea-108">[w] Przesunięcie sekcji.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-108">[in] The offset of the section.</span></span>  
  
 `relativeTo`  
 <span data-ttu-id="2b7ea-109">[w] Sekcja, do `offset` której się odnosi.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-109">[in] The section to which `offset` refers.</span></span>  
  
 `relocType`  
 <span data-ttu-id="2b7ea-110">[w] Jedna z wartości [CeeSectionRelocType,](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) wskazująca rodzaj instrukcji .reloc, aby dodać.</span><span class="sxs-lookup"><span data-stu-id="2b7ea-110">[in] One of the [CeeSectionRelocType](../../../../docs/framework/unmanaged-api/metadata/ceesectionreloctype-enumeration.md) values, indicating the kind of .reloc instruction to add.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b7ea-111">Wymagania</span><span class="sxs-lookup"><span data-stu-id="2b7ea-111">Requirements</span></span>  
 <span data-ttu-id="2b7ea-112">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b7ea-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b7ea-113">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="2b7ea-113">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="2b7ea-114">**Biblioteka:** Używany jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="2b7ea-114">**Library:** Used as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="2b7ea-115">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b7ea-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2b7ea-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2b7ea-116">See also</span></span>

- [<span data-ttu-id="2b7ea-117">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="2b7ea-117">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
