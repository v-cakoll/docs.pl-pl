---
title: CorRefToDefCheck — Wyliczenie
ms.date: 03/30/2017
api_name:
- CorRefToDefCheck
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorRefToDefCheck
helpviewer_keywords:
- CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 82abeb0ce3db075d794787bb1fcd5bc18321bef2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61906181"
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck — Wyliczenie
Określa flagi do kontroli, do którego istnieje odwołanie elementy, które są konwertowane na ich definicji w celu optymalizacji kodu.  
  
## <a name="syntax"></a>Składnia  
  
```  
typedef enum CorRefToDefCheck {  
    MDRefToDefDefault           = 0x00000003,  
    MDRefToDefAll               = 0xffffffff,  
    MDRefToDefNone              = 0x00000000,  
    MDTypeRefToDef              = 0x00000001,  
    MDMemberRefToDef            = 0x00000002  
} CorRefToDefCheck;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|`MDRefToDefDefault`|Określa, czy typ odwołania i odwołania do elementu członkowskiego powinny być konwertowane do definicji. Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Określa, że wszystkie elementy odwołania powinny być konwertowane do definicji.|  
|`MDRefToDefNone`|Określa, że żadne elementy odwołania powinny być konwertowane na definicje.|  
|`MDTypeRefToDef`|Określa, że tylko typ odwołania powinny być konwertowane na definicje typów.|  
|`MDMemberRefToDef`|Określa, że tylko odwołania do elementu członkowskiego powinny być konwertowane do definicji. Oznacza to, że odwołania do elementu członkowskiego powinny być konwertowane na definicje metod lub definicje pól.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
