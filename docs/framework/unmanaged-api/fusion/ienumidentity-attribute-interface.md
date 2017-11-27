---
title: "IEnumIDENTITY_ATTRIBUTE — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IEnumIDENTITY_ATTRIBUTE
api_location: fusion.dll
api_type: COM
f1_keywords: IEnumIDENTITY_ATTRIBUTE
helpviewer_keywords: IEnumIDENTITY_ATTRIBUTE interface [.NET Framework fusion]
ms.assetid: c2ec2748-e9ae-4e1b-80db-6fcec5cb81a1
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: f88e400556421e0908e0a0b115f66ec3221124c2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ienumidentityattribute-interface"></a>IEnumIDENTITY_ATTRIBUTE — Interfejs
Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IEnumIDENTITY_ATTRIBUTE::Clone`|Pobiera wskaźnika interfejsu na nowy `IEnumIDENTITY_ATTRIBUTE` zawierający członkowie to `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer`|Zapisuje dane zawarte w elementach to `IEnumIDENTITY_ATTRIBUTE` w buforze określone dane.|  
|`IEnumIDENTITY_ATTRIBUTE::Next`|Pobiera określoną liczbę atrybutów, zaczynając od bieżącego położenia.|  
|`IEnumIDENTITY_ATTRIBUTE::Reset`|Przesuwa wskaźnik instrukcji na początku `IEnumIDENTITY_ATTRIBUTE`.|  
|`IEnumIDENTITY_ATTRIBUTE::Skip`|Przenosi do przodu wskaźnik instrukcji przez określoną liczbę elementów, licząc w bieżącym położeniu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
