---
title: CeeSectionRelocType — Wyliczenie
ms.date: 03/30/2017
api_name:
- CeeSectionRelocType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CeeSectionRelocType
helpviewer_keywords:
- CeeSectionRelocType enumeration [.NET Framework metadata]
ms.assetid: 124656f6-0dad-4ceb-9043-d3869ab65cde
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 882242da493c49a2e6aa09888e9503dcf2933589
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59119590"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="ab7b3-102">CeeSectionRelocType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="ab7b3-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="ab7b3-103">Udostępnia wartości w celu wywierania wpływu na typ `reloc` instrukcji emitowane w wywołaniu [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="ab7b3-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7b3-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="ab7b3-104">Syntax</span></span>  
  
```  
typedef enum  {  
    srRelocAbsolute,  
    srRelocHighLow          = 3,  
    srRelocHighAdj,       
    srRelocMapToken,  
    srRelocRelative,  
    srRelocFilePos,  
    srRelocCodeRelative,  
    srRelocIA64Imm64,  
    srRelocDir64,  
    srRelocIA64PcRel25,  
    srRelocIA64PcRel64,    srRelocAbsoluteTagged,    srRelocSentinel,    srNoBaseReloc       = 0x4000,  
    srRelocPtr          = 0x8000,  
    srRelocAbsolutePtr      = srRelocPtr + srRelocAbsolute,  
    srRelocHighLowPtr       = srRelocPtr + srRelocHighLow,  
    srRelocRelativePtr      = srRelocPtr + srRelocRelative,  
    srRelocIA64Imm64Ptr     = srRelocPtr + srRelocIA64Imm64,  
    srRelocDir64Ptr         = srRelocPtr + srRelocDir64  
    } CeeSectionRelocType;  
```  
  
## <a name="members"></a><span data-ttu-id="ab7b3-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="ab7b3-105">Members</span></span>  
  
|<span data-ttu-id="ab7b3-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="ab7b3-106">Member</span></span>|<span data-ttu-id="ab7b3-107">Opis</span><span class="sxs-lookup"><span data-stu-id="ab7b3-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="ab7b3-108">Generuje tylko sekcję powiązane z wątkiem `reloc`, wysyłanie nothing do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="ab7b3-109">Generuje `reloc` dla lokalizacji wskaźnika wielkości.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="ab7b3-110">Ta konfiguracja jest przekształcana na BASED_HIGHLOW lub BASED_DIR64 zależności od platformy.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="ab7b3-111">Generuje `reloc` dla klauzuli top 16 bitów 32-bitową liczbą, gdzie dolnej 16 bitów są objęte następnego wyrazu w tabeli .reloc.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="ab7b3-112">Generuje przeniesienie mapy tokenów, nic nie wysyła do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="ab7b3-113">Wskazuje, czy wartość jest naprawy adresu względnego.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="ab7b3-114">Generuje tylko sekcję powiązane z wątkiem `reloc`, wysyłanie nothing do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="ab7b3-115">To `reloc` względem położenie pliku w sekcji, a nie w sekcji wirtualny adres.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="ab7b3-116">Określa naprawy adres względny kodu.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="ab7b3-117">Generuje `reloc` dla adresu 64-bitowych w ia64 `movl` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="ab7b3-118">Generuje `reloc` adres 64-bitowych.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="ab7b3-119">Generowanie `reloc` dla adresu względnego komputera 25-bitowych w ia64 `br.call` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="ab7b3-120">Generuje `reloc` dla adresu względnego komputera 64-bitowych w ia64 `brl.call` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="ab7b3-121">Generuje sekcji 30-bitowa — względna `reloc`, który jest używany dla wartości wskaźnika oznakowane.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="ab7b3-122">Wartość wartownik, aby pomóc w zapewnieniu wszystkie dodatki do tego typu wyliczeniowego są odzwierciedlane na wewnętrzny `reloc` tablicy nazwy.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="ab7b3-123">Określa, że nie Emituj podstawowej `reloc`.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="ab7b3-124">Wartość wskazującą, czy zawartości pre naprawy pamięci wskaźnika, a nie w sekcji przesunięcie.</span><span class="sxs-lookup"><span data-stu-id="ab7b3-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="ab7b3-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="ab7b3-125">Requirements</span></span>  
 <span data-ttu-id="ab7b3-126">**Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="ab7b3-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="ab7b3-127">**Nagłówek:** COR.h</span><span class="sxs-lookup"><span data-stu-id="ab7b3-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="ab7b3-128">**Biblioteka:** Dołączony jako zasób w MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="ab7b3-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="ab7b3-129">**Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="ab7b3-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ab7b3-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ab7b3-130">See also</span></span>

- [<span data-ttu-id="ab7b3-131">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="ab7b3-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="ab7b3-132">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="ab7b3-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="ab7b3-133">AddSectionReloc, metoda</span><span class="sxs-lookup"><span data-stu-id="ab7b3-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
