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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e909680428c7957da2283d13f5676329d953bf22
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67781897"
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr — Wyliczenie
Zawiera wartości, które opisują metadane dotyczące pola.  
  
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
|`fdPrivateScope`|Określa, że pole nie może być przywoływany.|  
|`fdPrivate`|Określa, że pole jest dostępne tylko dla typu nadrzędnego.|  
|`fdFamANDAssem`|Określa, że pole jest dostępny przez klasy pochodne w jego zestawie.|  
|`fdAssembly`|Określa, że pole jest dostępne dla wszystkich typów w jego zestawie.|  
|`fdFamily`|Określa, że pole jest dostępne tylko dla jego typu i klasach pochodnych.|  
|`fdFamORAssem`|Określa, że pole jest dostępne, przez klasy pochodne, jak również wszystkie typy w jego zestawie.|  
|`fdPublic`|Określa, że pole jest dostępne dla wszystkich typów za pomocą widoczność tego zakresu.|  
|`fdStatic`|Określa, że pole jest elementem członkowskim jego typu, a nie składową wystąpienia.|  
|`fdInitOnly`|Określa, że pole nie można zmienić po jego zainicjowaniu.|  
|`fdLiteral`|Określa, że wartość pola jest stałą czasu kompilacji.|  
|`fdNotSerialized`|Określa, czy pole nie jest serializowana, gdy jej typ jest zdalny.|  
|`fdSpecialName`|Określa, czy pole ma specjalne i że jego nazwę w tym artykule opisano sposób.|  
|`fdPinvokeImpl`|Określa, że implementacja pola jest przekazywany za pomocą usług PInvoke.|  
|`fdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`fdRTSpecialName`|Określa, że typowe metadanych środowiska wykonawczego języka wewnętrznych interfejsach API należy sprawdzać kodowanie nazwy.|  
|`fdHasFieldMarshal`|Określa, czy pole zawiera informacje dotyczące organizowania.|  
|`fdHasDefault`|Określa, że pole ma wartość domyślną.|  
|`fdHasFieldRVA`|Określa, że pole ma względny adres wirtualny.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
