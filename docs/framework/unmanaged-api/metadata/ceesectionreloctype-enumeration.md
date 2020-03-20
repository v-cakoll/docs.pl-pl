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
ms.openlocfilehash: 44a84e0752eecc1c694f3b8cf6e568b72b7d0f5c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176217"
---
# <a name="ceesectionreloctype-enumeration"></a><span data-ttu-id="3497f-102">CeeSectionRelocType — Wyliczenie</span><span class="sxs-lookup"><span data-stu-id="3497f-102">CeeSectionRelocType Enumeration</span></span>
<span data-ttu-id="3497f-103">Zawiera wartości wpływające `reloc` na typ instrukcji emitowanych w wywołaniu [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span><span class="sxs-lookup"><span data-stu-id="3497f-103">Provides values to influence the type of `reloc` instruction emitted in a call to [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3497f-104">Składnia</span><span class="sxs-lookup"><span data-stu-id="3497f-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="3497f-105">Elementy członkowskie</span><span class="sxs-lookup"><span data-stu-id="3497f-105">Members</span></span>  
  
|<span data-ttu-id="3497f-106">Członek</span><span class="sxs-lookup"><span data-stu-id="3497f-106">Member</span></span>|<span data-ttu-id="3497f-107">Opis</span><span class="sxs-lookup"><span data-stu-id="3497f-107">Description</span></span>|  
|------------|-----------------|  
|`srRelocAbsolute`|<span data-ttu-id="3497f-108">Generuje tylko względny `reloc`przekroju, nie przesyła niczego do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="3497f-108">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span>|  
|`srRelocHighLow`|<span data-ttu-id="3497f-109">Generuje `reloc` dla lokalizacji o rozmiarze wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="3497f-109">Generates a `reloc` for a pointer-sized location.</span></span> <span data-ttu-id="3497f-110">Jest to przekształcane w BASED_HIGHLOW lub BASED_DIR64 w zależności od platformy.</span><span class="sxs-lookup"><span data-stu-id="3497f-110">This is transformed into BASED_HIGHLOW or BASED_DIR64 depending on the platform.</span></span>|  
|`srRelocHighAdj`|<span data-ttu-id="3497f-111">Generuje `reloc` dla góry 16 bitów liczby 32-bitowej, gdzie dolne 16 bitów są zawarte w następnym słowie w tabeli .reloc.</span><span class="sxs-lookup"><span data-stu-id="3497f-111">Generates a `reloc` for the top 16 bits of a 32-bit number, where the bottom 16 bits are included in the next word in the .reloc table.</span></span>|  
|`srRelocMapToken`|<span data-ttu-id="3497f-112">Generuje przeniesienie mapy tokenu, nie wysyłając nic do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="3497f-112">Generates a token map relocation, sending nothing into a .reloc section.</span></span>|  
|`srRelocRelative`|<span data-ttu-id="3497f-113">Wskazuje, że wartość jest korektą adresu względnego.</span><span class="sxs-lookup"><span data-stu-id="3497f-113">Indicates that the value is a relative address fixup.</span></span>|  
|`srRelocFilePos`|<span data-ttu-id="3497f-114">Generuje tylko względny `reloc`przekroju, nie przesyła niczego do sekcji .reloc.</span><span class="sxs-lookup"><span data-stu-id="3497f-114">Generates only a section-relative `reloc`, sending nothing into a .reloc section.</span></span> <span data-ttu-id="3497f-115">Jest `reloc` to związane z położeniem pliku sekcji, a nie adresem wirtualnym sekcji.</span><span class="sxs-lookup"><span data-stu-id="3497f-115">This `reloc` is relative to the file position of the section, not the section's virtual address.</span></span>|  
|`srRelocCodeRelative`|<span data-ttu-id="3497f-116">Określa korektę adresu względnego kodu.</span><span class="sxs-lookup"><span data-stu-id="3497f-116">Specifies a code-relative address fixup.</span></span>|  
|`srRelocIA64Imm64`|<span data-ttu-id="3497f-117">Generuje `reloc` dla adresu 64-bitowego w instrukcji `movl` ia64.</span><span class="sxs-lookup"><span data-stu-id="3497f-117">Generates a `reloc` for a 64 bit address in an ia64 `movl` instruction.</span></span>|  
|`srRelocDir64`|<span data-ttu-id="3497f-118">Generuje `reloc` dla adresu 64-bitowego.</span><span class="sxs-lookup"><span data-stu-id="3497f-118">Generates a `reloc` for a 64-bit address.</span></span>|  
|`srRelocIA64PcRel25`|<span data-ttu-id="3497f-119">Wygeneruj `reloc` dla 25-bitowego adresu względnego `br.call` komputera w instrukcji ia64.</span><span class="sxs-lookup"><span data-stu-id="3497f-119">Generate a `reloc` for a 25-bit PC-relative address in an ia64 `br.call` instruction.</span></span>|  
|`srRelocIA64PcRel64`|<span data-ttu-id="3497f-120">Generuje `reloc` dla 64-bitowy adres względny komputera w `brl.call` instrukcji ia64.</span><span class="sxs-lookup"><span data-stu-id="3497f-120">Generates a `reloc` for a 64-bit PC-relative address in an ia64 `brl.call` instruction.</span></span>|  
|`srRelocAbsoluteTagged`|<span data-ttu-id="3497f-121">Generuje 30-bitową sekcję `reloc`względną, używaną dla oznakowanych wartości wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="3497f-121">Generates a 30-bit section-relative `reloc`, used for tagged pointer values.</span></span>|  
|`srRelocSentinel`|<span data-ttu-id="3497f-122">Wartość wartownika, aby zapewnić wszelkie dodatki do tego `reloc` wyliczenia są odzwierciedlane do wewnętrznej tablicy nazw.</span><span class="sxs-lookup"><span data-stu-id="3497f-122">A sentinel value to help ensure any additions to this enum are reflected to the internal `reloc` name array.</span></span>|  
|`srNoBaseReloc`|<span data-ttu-id="3497f-123">Określa, że nie `reloc`emituje bazy .</span><span class="sxs-lookup"><span data-stu-id="3497f-123">Specifies not to emit a base `reloc`.</span></span>|  
|`srRelocPtr`|<span data-ttu-id="3497f-124">Wartość wskazująca, że zawartość pamięci wstępnego korekty jest wskaźnikiem, a nie przesunięciem sekcji.</span><span class="sxs-lookup"><span data-stu-id="3497f-124">A value indicating that the pre-fixup contents of memory are a pointer rather than a section offset.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3497f-125">Wymagania</span><span class="sxs-lookup"><span data-stu-id="3497f-125">Requirements</span></span>  
 <span data-ttu-id="3497f-126">**Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3497f-126">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3497f-127">**Nagłówek:** Okręg wyborczy Cor.h</span><span class="sxs-lookup"><span data-stu-id="3497f-127">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3497f-128">**Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3497f-128">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3497f-129">**Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3497f-129">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3497f-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3497f-130">See also</span></span>

- [<span data-ttu-id="3497f-131">Wyliczenia metadanych</span><span class="sxs-lookup"><span data-stu-id="3497f-131">Metadata Enumerations</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [<span data-ttu-id="3497f-132">ICeeGen — Interfejs</span><span class="sxs-lookup"><span data-stu-id="3497f-132">ICeeGen Interface</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [<span data-ttu-id="3497f-133">AddSectionReloc — Metoda</span><span class="sxs-lookup"><span data-stu-id="3497f-133">AddSectionReloc Method</span></span>](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
