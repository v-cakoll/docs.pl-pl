---
title: "CorSymAddrKind — Wyliczenie"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 300913f9ea89044e425f9f05856d13fa15cdc015
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
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
 **Nagłówek:** CorSym.idl, CorSym.h  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia magazynu symboli diagnostycznych](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-enumerations.md)
