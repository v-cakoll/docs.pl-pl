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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType — Wyliczenie
Zawiera wartości wpływające `reloc` na typ instrukcji emitowanych w wywołaniu [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Generuje tylko względny `reloc`przekroju, nie przesyła niczego do sekcji .reloc.|  
|`srRelocHighLow`|Generuje `reloc` dla lokalizacji o rozmiarze wskaźnika. Jest to przekształcane w BASED_HIGHLOW lub BASED_DIR64 w zależności od platformy.|  
|`srRelocHighAdj`|Generuje `reloc` dla góry 16 bitów liczby 32-bitowej, gdzie dolne 16 bitów są zawarte w następnym słowie w tabeli .reloc.|  
|`srRelocMapToken`|Generuje przeniesienie mapy tokenu, nie wysyłając nic do sekcji .reloc.|  
|`srRelocRelative`|Wskazuje, że wartość jest korektą adresu względnego.|  
|`srRelocFilePos`|Generuje tylko względny `reloc`przekroju, nie przesyła niczego do sekcji .reloc. Jest `reloc` to związane z położeniem pliku sekcji, a nie adresem wirtualnym sekcji.|  
|`srRelocCodeRelative`|Określa korektę adresu względnego kodu.|  
|`srRelocIA64Imm64`|Generuje `reloc` dla adresu 64-bitowego w instrukcji `movl` ia64.|  
|`srRelocDir64`|Generuje `reloc` dla adresu 64-bitowego.|  
|`srRelocIA64PcRel25`|Wygeneruj `reloc` dla 25-bitowego adresu względnego `br.call` komputera w instrukcji ia64.|  
|`srRelocIA64PcRel64`|Generuje `reloc` dla 64-bitowy adres względny komputera w `brl.call` instrukcji ia64.|  
|`srRelocAbsoluteTagged`|Generuje 30-bitową sekcję `reloc`względną, używaną dla oznakowanych wartości wskaźnika.|  
|`srRelocSentinel`|Wartość wartownika, aby zapewnić wszelkie dodatki do tego `reloc` wyliczenia są odzwierciedlane do wewnętrznej tablicy nazw.|  
|`srNoBaseReloc`|Określa, że nie `reloc`emituje bazy .|  
|`srRelocPtr`|Wartość wskazująca, że zawartość pamięci wstępnego korekty jest wskaźnikiem, a nie przesunięciem sekcji.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [Wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Okręg wyborczy Cor.h  
  
 **Biblioteka:** Uwzględnione jako zasób w pliku MsCorEE.dll  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen — Interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc — Metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
