---
title: "CorRefToDefCheck — Wyliczenie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorRefToDefCheck
api_location: mscoree.dll
api_type: COM
f1_keywords: CorRefToDefCheck
helpviewer_keywords: CorRefToDefCheck enumeration [.NET Framework metadata]
ms.assetid: f9a80f1a-55af-4459-b095-8441aae16119
topic_type: apiref
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5144cd3ac261647c04ec7e3e27e28618c94fb439
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="correftodefcheck-enumeration"></a>CorRefToDefCheck — Wyliczenie
Określa flagi kontrolujące elementy do którego istnieje odwołanie, które są konwertowane na ich definicje w celu optymalizacji kodu.  
  
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
|`MDRefToDefDefault`|Określa, że odwołania do typu i odwołania do elementu członkowskiego powinny być konwertowane do definicji. Jest to wartość domyślna (`MDTypeRefToDef` &#124; `MDMemberRefToDef`).|  
|`MDRefToDefAll`|Określa, że wszystkie elementy z którym związane są odwołania powinny być konwertowane do definicji.|  
|`MDRefToDefNone`|Określa, że nie przywoływanych elementów powinny być konwertowane do definicji.|  
|`MDTypeRefToDef`|Określa, że tylko odwołania do typu powinny być konwertowane na typ definicje.|  
|`MDMemberRefToDef`|Określa, że tylko odwołania do elementu członkowskiego powinny być konwertowane do definicji. Oznacza to, że odwołania do elementu członkowskiego powinny być konwertowane na definicjami metod lub definicje pól.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorHdr.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Wyliczenia metadanych](../../../../docs/framework/unmanaged-api/metadata/metadata-enumerations.md)
