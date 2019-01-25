---
title: CorPropertyAttr — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorPropertyAttr
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorPropertyAttr
helpviewer_keywords:
- CorPropertyAttr enumeration [.NET Framework metadata]
ms.assetid: 58ac8202-854d-4efd-acfb-d2da8b446e12
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 713913fa046fc1bef12b8849ac82e4399a8dc534
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54577587"
---
# <a name="corpropertyattr-enumeration"></a>CorPropertyAttr — Wyliczenie
Zawiera wartości, które opisują metadane właściwości.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorPropertyAttr {  
  
    prSpecialName           =   0x0200,   
    prReservedMask          =   0xf400,  
    prRTSpecialName         =   0x0400,  
    prHasDefault            =   0x1000,  
    prUnused                =   0xe9ff  
  
} CorPropertyAttr;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`prSpecialName`|Określa, czy właściwość jest specjalne i że jego nazwę w tym artykule opisano sposób.|  
|`prReservedMask`|Zarezerwowane do użytku wewnętrznego przez środowisko uruchomieniowe języka wspólnego.|  
|`prRTSpecialName`|Określa, że typowe metadanych środowiska wykonawczego języka wewnętrznych interfejsach API należy sprawdzać kodowanie nazwy właściwości.|  
|`prHasDefault`|Określa, że właściwość ma wartość domyślną.|  
|`prUnused`|Nieużywane.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
