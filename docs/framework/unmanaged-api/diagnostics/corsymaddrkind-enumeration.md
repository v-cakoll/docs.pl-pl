---
title: CorSymAddrKind — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorSymAddrKind
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorSymAddrKind
helpviewer_keywords:
- CorSymAddrKind enumeration [.NET Framework debugging]
ms.assetid: 3ef841c2-cade-42ee-ba34-2ef91d6d0879
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 98cf49714829b4b2f80e0240c2ebde7fa6c280e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind — Wyliczenie
Wskazuje typ adres pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorSymAddrKind  
{  
    ADDR_IL_OFFSET          = 1,  
    ADDR_NATIVE_RVA         = 2,  
    ADDR_NATIVE_REGISTER    = 3,  
    ADDR_NATIVE_REGREL      = 4,  
    ADDR_NATIVE_OFFSET      = 5,  
    ADDR_NATIVE_REGREG      = 6,  
    ADDR_NATIVE_REGSTK      = 7,  
    ADDR_NATIVE_STKREG      = 8,  
    ADDR_BITFIELD           = 9,  
    ADDR_NATIVE_ISECTOFFSET = 10  
} CorSymAddrKind;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Wskazuje Microsoft język pośredni (MSIL) lokalnej zmiennej lub parametru indeks.|  
|`ADDR_NATIVE_RVA`|Wskazuje wirtualny adres względny w module.|  
|`ADDR_NATIVE_REGISTER`|Wskazuje rejestru procesora CPU.|  
|`ADDR_NATIVE_REGREL`|Wskazuje, że pierwszy adres jest rejestr i drugi adres jest przesunięcia.|  
|`ADDR_NATIVE_OFFSET`|Określa przesunięcie od adres podstawowy.|  
|`ADDR_NATIVE_REGREG`|Wskazuje, że pierwszy adres jest niski część rejestru i drugi adres jest wysoki.|  
|`ADDR_NATIVE_REGSTK`|Wskazuje, że pierwszy adres jest niski część rejestr, drugi ma wysoką części i trzeci jest przesunięcia.|  
|`ADDR_NATIVE_STKREG`|Wskazuje, że rejestr jest pierwszym adresem, przesunięcie jest drugi i trzeci jest wysoka części rejestru.|  
|`ADDR_BITFIELD`|Wskazuje, że pierwszy adres jest początek pola i drugi adres jest długość pola.|  
|`ADDR_NATIVE_ISECTOFFSET`|Wskazuje, że sekcja jest pierwszym adresem i drugi adres jest przesunięcia.|  
  
## <a name="requirements"></a>Wymagania  
 **Header:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
