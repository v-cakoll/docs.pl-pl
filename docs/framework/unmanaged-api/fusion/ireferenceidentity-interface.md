---
title: "IReferenceIdentity — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IReferenceIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IReferenceIdentity
helpviewer_keywords: IReferenceIdentity interface [.NET Framework fusion]
ms.assetid: 9180ac5a-7019-4716-9f83-8a91d157239a
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 35c6152836adf02d541bacd149ed9ac053765ba6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ireferenceidentity-interface"></a>IReferenceIdentity — Interfejs
Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IReferenceIdentity::Clone`|Pobiera wskaźnika interfejsu na nowy `IReferenceIdentity` wystąpienia, który jest taki sam jak to `IReferenceIdentity`, z wyjątkiem zmiany określonego atrybutu.|  
|`IReferenceIdentity::EnumAttributes`|Pobiera wskaźnika interfejsu do `IEnumIDENTITY_ATTRIBUTE` wystąpienia, które zawiera atrybuty skojarzone z tym `IReferenceIdentity`.|  
|`IReferenceIdentity::GetAttribute`|Pobiera wartość atrybutu w określonej przestrzeni nazw o określonej nazwie.|  
|`IReferenceIdentity::SetAttribute`|Ustawia atrybut, który ma określonego obszaru nazw i nazwę określonego na określoną wartość.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)  
 [Ienumidentity_attribute — interfejs](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
