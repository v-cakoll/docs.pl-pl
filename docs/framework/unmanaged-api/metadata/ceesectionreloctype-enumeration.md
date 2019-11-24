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
ms.openlocfilehash: efce0c13944b383c42cbff6a6af4795293ee2989
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74444157"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="a8348-102">CeeSectionRelocType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="a8348-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="a8348-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="a8348-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8348-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="a8348-104">Syntax</span></span>  
  
```cpp  
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
  
## <a name="members"></a><span data-ttu-id="a8348-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="a8348-105">Members</span></span>  
  
|<span data-ttu-id="a8348-106">Element członkowski</span><span class="sxs-lookup"><span data-stu-id="a8348-106">Member</span></span>|<span data-ttu-id="a8348-107">Opis</span><span class="sxs-lookup"><span data-stu-id="a8348-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="a8348-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="a8348-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="a8348-109">Generates a `reloc` for a pointer-sized location.</span><span class="sxs-lookup"><span data-stu-id="a8348-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="a8348-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span><span class="sxs-lookup"><span data-stu-id="a8348-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="a8348-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span><span class="sxs-lookup"><span data-stu-id="a8348-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="a8348-112">Generates a token map relocation, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="a8348-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="a8348-113">Indicates that the value is a relative address fixup.</span><span class="sxs-lookup"><span data-stu-id="a8348-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="a8348-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span><span class="sxs-lookup"><span data-stu-id="a8348-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="a8348-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span><span class="sxs-lookup"><span data-stu-id="a8348-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="a8348-116">Specifies a code-relative address fixup.</span><span class="sxs-lookup"><span data-stu-id="a8348-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="a8348-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span><span class="sxs-lookup"><span data-stu-id="a8348-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="a8348-118">Generates a `reloc` for a 64-bit address.</span><span class="sxs-lookup"><span data-stu-id="a8348-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="a8348-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="a8348-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="a8348-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span><span class="sxs-lookup"><span data-stu-id="a8348-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="a8348-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span><span class="sxs-lookup"><span data-stu-id="a8348-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="a8348-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span><span class="sxs-lookup"><span data-stu-id="a8348-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="a8348-123">Specifies not to emit a base `reloc`.</span><span class="sxs-lookup"><span data-stu-id="a8348-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="a8348-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span><span class="sxs-lookup"><span data-stu-id="a8348-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a8348-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="a8348-125">Requirements</span></span>  
 <span data-ttu-id="a8348-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a8348-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a8348-127">**Header:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="a8348-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="a8348-128">**Library:** Included as a resource in MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="a8348-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="a8348-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a8348-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8348-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a8348-130">See also</span></span>

- [<span data-ttu-id="a8348-131">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="a8348-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="a8348-132">ICeeGen, interfejs</span><span class="sxs-lookup"><span data-stu-id="a8348-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="a8348-133">AddSectionReloc, metoda</span><span class="sxs-lookup"><span data-stu-id="a8348-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
