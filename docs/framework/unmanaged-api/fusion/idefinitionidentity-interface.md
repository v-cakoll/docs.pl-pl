---
title: "IDefinitionIdentity — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionIdentity
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionIdentity
helpviewer_keywords: IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b074ae2a0a4e4e65f0402ff35888b557b00dd071
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity — Interfejs
Reprezentuje podpis unikatowy kod, który definiuje aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Pobiera wskaźnika interfejsu na nowy `IDefinitionIdentity` obiekt, który jest taki sam jak to `IDefinitionIdentity`, z wyjątkiem zmiany określonego atrybutu.|  
|`IDefinitionIdentity::EnumAttributes`|Pobiera wskaźnika interfejsu do [ienumidentity_attribute —](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) obiekt zawierający atrybuty skojarzone z tym `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Pobiera wartość atrybutu o określonej nazwie w określonej przestrzeni nazw.|  
|`IDefinitionIdentity::SetAttribute`|Ustawia atrybut, który ma określoną nazwę w określonej przestrzeni nazw z podaną wartością.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
