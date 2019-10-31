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
ms.openlocfilehash: 59578e1d3a66809c86f7daad1b208df2ae09568d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108037"
---
# <a name="idefinitionidentity-interface"></a>IDefinitionIdentity — Interfejs
Reprezentuje unikatowy podpis kodu, który definiuje aplikację w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionIdentity::Clone`|Pobiera wskaźnik interfejsu do nowego obiektu `IDefinitionIdentity`, który jest identyczny z tym `IDefinitionIdentity`, z wyjątkiem określonych zmian atrybutów.|  
|`IDefinitionIdentity::EnumAttributes`|Pobiera wskaźnik interfejsu do obiektu [IEnumIDENTITY_ATTRIBUTE](ienumidentity-attribute-interface.md) , który zawiera atrybuty skojarzone z tym `IDefinitionIdentity`.|  
|`IDefinitionIdentity::GetAttribute`|Pobiera wartość atrybutu o określonej nazwie w określonym obszarze nazw.|  
|`IDefinitionIdentity::SetAttribute`|Ustawia atrybut, który ma określoną nazwę w określonym obszarze nazw do określonej wartości.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
