---
title: "CeeSectionRelocType — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: d257778a9a05e2654d7f91c0205424d001f5ae3e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ceesectionreloctype-enumeration"></a>CeeSectionRelocType — Wyliczenie
Udostępnia wartości w celu wywierania wpływu typ `reloc` instrukcji wysyłanego w wywołaniu [ICeeGen::AddSectionReloc](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md).  
  
## <a name="syntax"></a>Składnia  
  
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
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`srRelocAbsolute`|Generuje tylko sekcji względnego `reloc`, wysyłania nic do sekcji .reloc.|  
|`srRelocHighLow`|Generuje `reloc` dla lokalizacji o rozmiarze wskaźnika. To jest przekształcana na BASED_HIGHLOW lub BASED_DIR64 w zależności od platformy.|  
|`srRelocHighAdj`|Generuje `reloc` dla pierwszych 16 bitów 32-bitową liczbą, gdzie dolnej 16 bitów znajdują się w następnej programu word w tabeli .reloc.|  
|`srRelocMapToken`|Generuje przeniesienie mapy tokenów, wysyłanie nic do sekcji .reloc.|  
|`srRelocRelative`|Wskazuje, czy wartość jest naprawy adres względny.|  
|`srRelocFilePos`|Generuje tylko sekcji względnego `reloc`, wysyłania nic do sekcji .reloc. To `reloc` jest określana względem położenie pliku sekcji, a nie adresów wirtualnych sekcji.|  
|`srRelocCodeRelative`|Określa naprawy adres względny kodu.|  
|`srRelocIA64Imm64`|Generuje `reloc` dla adresu 64-bitowe w ia64 `movl` instrukcji.|  
|`srRelocDir64`|Generuje `reloc` dla 64-bitowy adres.|  
|`srRelocIA64PcRel25`|Generowanie `reloc` dla adresu względnego komputera 25-bitowe w ia64 `br.call` instrukcji.|  
|`srRelocIA64PcRel64`|Generuje `reloc` dla adresu względnego komputera 64-bitowe w ia64 `brl.call` instrukcji.|  
|`srRelocAbsoluteTagged`|Generuje względnego sekcji 30-bitowa `reloc`, używana dla wartości wskaźników oznakowanych.|  
|`srRelocSentinel`|Wartość wartownik w celu zapewnienia wszystkie dodatki do tego wyliczenia są uwzględniane do wewnętrznej `reloc` tablicy nazwy.|  
|`srNoBaseReloc`|Określa, że nie Emituj podstawowej `reloc`.|  
|`srRelocPtr`|Wartość wskazującą, czy zawartość sprzed naprawy pamięci wskaźnik zamiast sekcji przesunięcie.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Cor.h  
  
 **Biblioteka:** uwzględnione jako zasób w MsCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)  
 [ICeeGen, interfejs](../../../../docs/framework/unmanaged-api/metadata/iceegen-interface.md)  
 [AddSectionReloc, metoda](../../../../docs/framework/unmanaged-api/metadata/iceegen-addsectionreloc-method.md)
