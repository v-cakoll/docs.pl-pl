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
ms.openlocfilehash: 78b30f624bd71234e8f1b56600b3a23d15fdf517
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006038"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType — Wyliczenie
Dostarcza wartości mające wpływ na typ `reloc` instrukcji emitowanej w wywołaniu [ICeeGen:: AddSectionReloc —](iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Członek|Opis|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje tylko odwołanie względne `reloc` do sekcji, wysyłając Nothing do sekcji. reloc.|  
|`srRelocHighLow`|Generuje `reloc` dla lokalizacji wskaźnika. Jest on przekształcany w BASED_HIGHLOW lub BASED_DIR64 w zależności od platformy.|  
|`srRelocHighAdj`|Generuje `reloc` dla pierwszych 16 bitów o 32-bitowej liczbie, gdzie ostatnie 16 bitów jest uwzględnionych w następnym wyrazie w tabeli. reloc.|  
|`srRelocMapToken`|Generuje relokację mapy tokenów, wysyłając nic do sekcji. reloc.|  
|`srRelocRelative`|Wskazuje, że wartość jest korektą adresu względnego.|  
|`srRelocFilePos`|Generuje tylko odwołanie względne `reloc` do sekcji, wysyłając Nothing do sekcji. reloc. `reloc`Jest to względne względem położenia pliku sekcji, a nie adresu wirtualnego sekcji.|  
|`srRelocCodeRelative`|Określa naprawianie adresów względnych w kodzie.|  
|`srRelocIA64Imm64`|Generuje `reloc` dla adresu 64 bitowego w `movl` instrukcji ia64.|  
|`srRelocDir64`|Generuje `reloc` dla adresu 64-bitowego.|  
|`srRelocIA64PcRel25`|Wygeneruj `reloc` adres 25-bitowy względem komputera w `br.call` instrukcji ia64.|  
|`srRelocIA64PcRel64`|Generuje wartość `reloc` dla 64-bitowego adresu komputera w `brl.call` instrukcji ia64.|  
|`srRelocAbsoluteTagged`|Generuje 30-bitową względną sekcję `reloc` , używaną dla oznakowanych wartości wskaźnika.|  
|`srRelocSentinel`|Wartość wskaźnikowa, która pomaga zapewnić, że wszelkie dodatki do tego wyliczenia są odzwierciedlone w wewnętrznej `reloc` tablicy nazw.|  
|`srNoBaseReloc`|Określa, że nie ma być emitowana baza `reloc` .|  
|`srRelocPtr`|Wartość wskazująca, że przed przemieszczeniem sekcji jest wskaźnik, a nie przesunięty sekcję.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](metadata-enumerations.md)
- [ICeeGen — Interfejs](iceegen-interface.md)
- [AddSectionReloc — Metoda](iceegen-addsectionreloc-method.md)
