---
title: "CorFieldAttr — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorFieldAttr
api_location: mscoree.dll
api_type: COM
f1_keywords: CorFieldAttr
helpviewer_keywords: CorFieldAttr enumeration [.NET Framework metadata]
ms.assetid: 6ae2c4be-212c-4e74-9288-40a11dc26522
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b5128ea59f7668737885835723156fc7f1786872
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="corfieldattr-enumeration"></a>CorFieldAttr — Wyliczenie
Zawiera wartości, które opisują metadanych pola.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|`fdPrivateScope`|Określa, czy pole nie może być przywoływany.|  
|`fdPrivate`|Określa, że pole jest dostępne tylko dla jego typu nadrzędnego.|  
|`fdFamANDAssem`|Określa, że pole jest dostępne dla klas pochodnych w jego zestaw.|  
|`fdAssembly`|Określa, że pole jest dostępne dla wszystkich typów w zestawie jej.|  
|`fdFamily`|Określa, czy pole jest dostępne tylko dla jego typu i klasach pochodnych.|  
|`fdFamORAssem`|Określa, czy pole jest dostępny, za pomocą klasy pochodne i wszystkie typy w jego zestaw.|  
|`fdPublic`|Określa, że pole jest dostępne dla wszystkich typów z widocznością tego zakresu.|  
|`fdStatic`|Określa, że pole jest elementem członkowskim jego typu, a nie elementu członkowskiego wystąpienia.|  
|`fdInitOnly`|Określa, że nie można zmienić pola po jego inicjowania.|  
|`fdLiteral`|Określa, czy wartość pola jest stałą czasu kompilacji.|  
|`fdNotSerialized`|Określa, czy pole nie jest serializowany, gdy jej typ jest zdalny.|  
|`fdSpecialName`|Określa, czy pole ma specjalne i że jego nazwa zawiera opis sposobu.|  
|`fdPinvokeImpl`|Określa, że implementacja pole jest przekazywany za pomocą funkcji PInvoke.|  
|`fdReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`fdRTSpecialName`|Określa, że typowe metadane środowiska wykonawczego języka wewnętrznych interfejsów API należy sprawdzać kodowanie nazwy.|  
|`fdHasFieldMarshal`|Określa, czy pole zawiera informacji organizacyjnych.|  
|`fdHasDefault`|Określa, czy pole ma wartość domyślną.|  
|`fdHasFieldRVA`|Określa, czy pole ma wirtualnego adresu względnego.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
