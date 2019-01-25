---
title: IDefinitionIdentity — Interfejs
ms.date: 03/30/2017
api_name:
- IDefinitionIdentity
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionIdentity
helpviewer_keywords:
- IDefinitionIdentity interface [.NET Framework fusion]
ms.assetid: ce5ba888-5fbe-4efd-91cf-f0ff94d8428b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: fb97c545d2d57ef589b5a7a5b3618eaa2b6f364f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54687001"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity — Interfejs
Reprezentuje unikatowy podpis kodu, który definiuje aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego `IDefinitionIdentity` obiektu, który jest identyczny z tym `IDefinitionIdentity`, z wyjątkiem zmiany określonego atrybutu.|  
|`IDefinitionIdentity::EnumAttributes`|Pobiera wskaźnik interfejsu do [ienumidentity_attribute —](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) obiekt, który zawiera atrybuty skojarzone z tym `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Pobiera wartość atrybutu o określonej nazwie w określonej przestrzeni nazw.|  
|`IDefinitionIdentity::SetAttribute`|Ustawia atrybut, który ma określoną nazwę w określonej przestrzeni nazw z podaną wartością.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
