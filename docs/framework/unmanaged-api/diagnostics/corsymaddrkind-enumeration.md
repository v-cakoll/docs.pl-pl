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
ms.openlocfilehash: 12f31d0bf224e38418818122dad3586ec687b2ad
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448579"
---
# <a name="corsymaddrkind-enumeration"></a>CorSymAddrKind — Wyliczenie
Wskazuje typ adresu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
  
## <a name="members"></a>Members  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`ADDR_IL_OFFSET`|Wskazuje zmienną lokalną języka pośredniego (MSIL) firmy Microsoft lub indeks parametru.|  
|`ADDR_NATIVE_RVA`|Wskazuje względny adres wirtualny do modułu.|  
|`ADDR_NATIVE_REGISTER`|Wskazuje rejestr procesora CPU.|  
|`ADDR_NATIVE_REGREL`|Wskazuje, że pierwszy adres jest rejestrem, a drugi adres jest przesunięty.|  
|`ADDR_NATIVE_OFFSET`|Wskazuje przesunięcie od adresu podstawowego.|  
|`ADDR_NATIVE_REGREG`|Wskazuje, że pierwszy adres jest małą częścią rejestru, a drugi adres jest dużą częścią.|  
|`ADDR_NATIVE_REGSTK`|Wskazuje, że pierwszy adres jest małą częścią rejestru, drugi jest dużą częścią, a trzeci jest przesunięciem.|  
|`ADDR_NATIVE_STKREG`|Wskazuje, że pierwszy adres jest rejestrem, drugi jest przesunięciem, a trzeci to wysoka część rejestru.|  
|`ADDR_BITFIELD`|Wskazuje, że pierwszy adres jest początkiem pola, a drugi adres jest długością pola.|  
|`ADDR_NATIVE_ISECTOFFSET`|Wskazuje, że pierwszy adres jest sekcją, a drugi adres jest przesunięciem.|  
  
## <a name="requirements"></a>Wymagania  
 **Nagłówek:** CorSym. idl, CorSym. h  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
