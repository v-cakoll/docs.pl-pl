---
title: IDefinitionAppId — Interfejs
ms.date: 03/30/2017
api_name:
- IDefinitionAppId
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDefinitionAppId
helpviewer_keywords:
- IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type:
- apiref
ms.openlocfilehash: 5114f74e80da925c7a153b9e481c54067152eaec
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73108198"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId — Interfejs
Reprezentuje unikatowy identyfikator kodu, który definiuje aplikację w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Pobiera sformatowany ciąg, który reprezentuje kod w tym obiekcie `IDefinitionAppId`.|  
|`IDefinitionAppId::put_Codebase`|Ustawia kod tego obiektu `IDefinitionAppId` na określoną wartość ciągu sformatowanego.|  
|`IDefinitionAppId::EnumAppPath`|Pobiera wskaźnik interfejsu do obiektu [IEnumDefinitionIdentity —](ienumdefinitionidentity-interface.md) , który zawiera zestawy w bieżącej ścieżce aplikacji.|  
|`IDefinitionAppId::SetAppPath`|Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie do wartości, do której odwołuje się określony obiekt [IDefinitionIdentity —](idefinitionidentity-interface.md) .|  
|`IDefinitionAppId::get_SubscriptionId`|Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji dla tego obiektu `IDefinitionAppId`.|  
|`IDefinitionAppId::put_SubscriptionId`|Ustawia identyfikator tokenu dla subskrypcji dla tego obiektu `IDefinitionAppId` na określoną wartość ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
