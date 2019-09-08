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
ms.openlocfilehash: 84c595bfdcca84ee43a53e2ea913cc978ae0953e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796526"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity — Interfejs
Reprezentuje unikatowy podpis kodu, który definiuje aplikację w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego `IDefinitionIdentity` obiektu, który jest identyczny z tym `IDefinitionIdentity`, z wyjątkiem określonych zmian atrybutów.|  
|`IDefinitionIdentity::EnumAttributes`|Pobiera wskaźnik interfejsu do obiektu [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , który zawiera atrybuty skojarzone z tym `IDefinitionIdentity`elementem.|  
|`IDefinitionIdentity::GetAttribute`|Pobiera wartość atrybutu o określonej nazwie w określonym obszarze nazw.|  
|`IDefinitionIdentity::SetAttribute`|Ustawia atrybut, który ma określoną nazwę w określonym obszarze nazw do określonej wartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
