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
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType — Wyliczenie
Dostarcza wartości mające wpływ na typ instrukcji `reloc` emitowany w wywołaniu [ICeeGen:: AddSectionReloc —](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje tylko `reloc`względną dla sekcji, co spowoduje wysłanie niczego do sekcji. reloc.|  
|`srRelocHighLow`|Generuje `reloc` dla lokalizacji wskaźnika. Jest on przekształcany w BASED_HIGHLOW lub BASED_DIR64 w zależności od platformy.|  
|`srRelocHighAdj`|Generuje `reloc` dla pierwszych 16 bitów liczby 32-bitowej, gdzie ostatnie 16 bitów znajduje się w następnym wyrazie w tabeli. reloc.|  
|`srRelocMapToken`|Generuje relokację mapy tokenów, wysyłając nic do sekcji. reloc.|  
|`srRelocRelative`|Wskazuje, że wartość jest korektą adresu względnego.|  
|`srRelocFilePos`|Generuje tylko `reloc`względną dla sekcji, co spowoduje wysłanie niczego do sekcji. reloc. Ta `reloc` jest określana względem pozycji pliku sekcji, a nie adresu wirtualnego sekcji.|  
|`srRelocCodeRelative`|Określa naprawianie adresów względnych w kodzie.|  
|`srRelocIA64Imm64`|Generuje `reloc` dla adresu bitowej 64 w instrukcji `movl` ia64.|  
|`srRelocDir64`|Generuje `reloc` dla adresu 64-bitowego.|  
|`srRelocIA64PcRel25`|Wygeneruj `reloc` w przypadku 25-bitowego adresu komputera w instrukcji `br.call` ia64.|  
|`srRelocIA64PcRel64`|Generuje `reloc` w przypadku 64-bitowego adresu z komputera w instrukcji `brl.call` ia64.|  
|`srRelocAbsoluteTagged`|Generuje 30-bitową `reloc`względną dla sekcji służącą do oznakowania wartości wskaźnika.|  
|`srRelocSentinel`|Wartość wskaźnikowa, która pomaga zapewnić, że wszelkie dodatki do tego wyliczenia są odzwierciedlone w wewnętrznej tablicy nazw `reloc`.|  
|`srNoBaseReloc`|Określa, że nie należy emitować `reloc`podstawowej.|  
|`srRelocPtr`|Wartość wskazująca, że przed przemieszczeniem sekcji jest wskaźnik, a nie przesunięty sekcję.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MsCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
