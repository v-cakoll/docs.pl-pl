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
ms.openlocfilehash: 1218ee76a3b7a2f501f87adf1e0bc8133d5329b5
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781346"
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType — Wyliczenie
Udostępnia wartości w celu wywierania wpływu na typ `reloc` instrukcji emitowane w wywołaniu [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
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
|`srRelocAbsolute`|Generuje tylko sekcję powiązane z wątkiem `reloc`, wysyłanie nothing do sekcji .reloc.|  
|`srRelocHighLow`|Generuje `reloc` dla lokalizacji wskaźnika wielkości. Ta konfiguracja jest przekształcana na BASED_HIGHLOW lub BASED_DIR64 zależności od platformy.|  
|`srRelocHighAdj`|Generuje `reloc` dla klauzuli top 16 bitów 32-bitową liczbą, gdzie dolnej 16 bitów są objęte następnego wyrazu w tabeli .reloc.|  
|`srRelocMapToken`|Generuje przeniesienie mapy tokenów, nic nie wysyła do sekcji .reloc.|  
|`srRelocRelative`|Wskazuje, czy wartość jest naprawy adresu względnego.|  
|`srRelocFilePos`|Generuje tylko sekcję powiązane z wątkiem `reloc`, wysyłanie nothing do sekcji .reloc. To `reloc` względem położenie pliku w sekcji, a nie w sekcji wirtualny adres.|  
|`srRelocCodeRelative`|Określa naprawy adres względny kodu.|  
|`srRelocIA64Imm64`|Generuje `reloc` dla adresu 64-bitowych w ia64 `movl` instrukcji.|  
|`srRelocDir64`|Generuje `reloc` adres 64-bitowych.|  
|`srRelocIA64PcRel25`|Generowanie `reloc` dla adresu względnego komputera 25-bitowych w ia64 `br.call` instrukcji.|  
|`srRelocIA64PcRel64`|Generuje `reloc` dla adresu względnego komputera 64-bitowych w ia64 `brl.call` instrukcji.|  
|`srRelocAbsoluteTagged`|Generuje sekcji 30-bitowa — względna `reloc`, który jest używany dla wartości wskaźnika oznakowane.|  
|`srRelocSentinel`|Wartość wartownik, aby pomóc w zapewnieniu wszystkie dodatki do tego typu wyliczeniowego są odzwierciedlane na wewnętrzny `reloc` tablicy nazwy.|  
|`srNoBaseReloc`|Określa, że nie Emituj podstawowej `reloc`.|  
|`srRelocPtr`|Wartość wskazującą, czy zawartości pre naprawy pamięci wskaźnika, a nie w sekcji przesunięcie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** COR.h  
  
 **Biblioteka:** Dołączony jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
- [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)
- [AddSectionReloc, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
