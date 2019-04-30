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
ms.openlocfilehash: 4ff23330f307c10eac134048de39a6e19a67c75b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697540"
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
