---
title: CorFieldAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorFieldAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorFieldAttr
helpviewer_keywords:
- CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type:
- apiref
ms.openlocfilehash: d28a0c8b7ee85f023026dde6f3cc8f3a8406aa64
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450305"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr — Wyliczenie
Zawiera wartości opisujące metadane dotyczące pola.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorFieldAttr {  
  
    fdFieldAccessMask           =   0x0007,  
    fdPrivateScope              =   0x0000,  
    fdPrivate                   =   0x0001,  
    fdFamANDAssem               =   0x0002,  
    fdAssembly                  =   0x0003,  
    fdFamily                    =   0x0004,  
    fdFamORAssem                =   0x0005,  
    fdPublic                    =   0x0006,  
  
    fdStatic                    =   0x0010,  
    fdInitOnly                  =   0x0020,  
    fdLiteral                   =   0x0040,  
    fdNotSerialized             =   0x0080,  
  
    fdSpecialName               =   0x0200,  
  
    fdPinvokeImpl               =   0x2000,  
  
    fdReservedMask              =   0x9500,  
    fdRTSpecialName             =   0x0400,  
    fdHasFieldMarshal           =   0x1000,  
    fdHasDefault                =   0x8000,  
    fdHasFieldRVA               =   0x0100  
  
} CorFieldAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`fdFieldAccessMask`|Określa informacje o ułatwieniach dostępu.|  
|`fdPrivateScope`|Określa, że nie można odwołać się do pola.|  
|`fdPrivate`|Określa, że pole jest dostępne tylko dla jego typu nadrzędnego.|  
|`fdFamANDAssem`|Określa, że pole jest dostępne dla klas pochodnych w zestawie.|  
|`fdAssembly`|Określa, że pole jest dostępne dla wszystkich typów w zestawie.|  
|`fdFamily`|Określa, że pole jest dostępne tylko na podstawie jego typu i klas pochodnych.|  
|`fdFamORAssem`|Określa, że pole jest dostępne dla klas pochodnych i wszystkich typów w zestawie.|  
|`fdPublic`|Określa, że pole jest dostępne dla wszystkich typów z widocznością tego zakresu.|  
|`fdStatic`|Określa, że pole jest elementem członkowskim typu, a nie elementem członkowskim wystąpienia.|  
|`fdInitOnly`|Określa, że nie można zmienić pola po jego zainicjowaniu.|  
|`fdLiteral`|Określa, że wartość pola jest stałą czasu kompilacji.|  
|`fdNotSerialized`|Określa, że pole nie jest serializowane, gdy jego typ jest zdalny.|  
|`fdSpecialName`|Określa, że pole jest specjalne i że jego nazwa opisuje sposób.|  
|`fdPinvokeImpl`|Określa, że implementacja pola jest przekazywana za pomocą funkcji PInvoke.|  
|`fdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`fdRTSpecialName`|Określa, że wewnętrzne interfejsy API środowiska uruchomieniowego języka wspólnego powinny sprawdzać kodowanie nazwy.|  
|`fdHasFieldMarshal`|Określa, że pole zawiera informacje o kierowaniu.|  
|`fdHasDefault`|Określa, że pole ma wartość domyślną.|  
|`fdHasFieldRVA`|Określa, że pole ma względny adres wirtualny.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
