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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 929909a7f2c4fa1799c8fed94787b8f853c7eac2
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796520"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId — Interfejs
Reprezentuje unikatowy identyfikator kodu, który definiuje aplikację w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Pobiera sformatowany ciąg, który reprezentuje kod w tym `IDefinitionAppId` obiekcie.|  
|`IDefinitionAppId::put_Codebase`|Ustawia kod tego `IDefinitionAppId` obiektu na określoną wartość ciągu sformatowanego.|  
|`IDefinitionAppId::EnumAppPath`|Pobiera wskaźnik interfejsu do obiektu [IEnumDefinitionIdentity —](ienumdefinitionidentity-interface.md) , który zawiera zestawy w bieżącej ścieżce aplikacji.|  
|`IDefinitionAppId::SetAppPath`|Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie do wartości, do której odwołuje się określony obiekt [IDefinitionIdentity —](idefinitionidentity-interface.md) .|  
|`IDefinitionAppId::get_SubscriptionId`|Pobiera wskaźnik do ciągu reprezentującego Identyfikator tokenu dla subskrypcji dla tego `IDefinitionAppId` obiektu.|  
|`IDefinitionAppId::put_SubscriptionId`|Ustawia identyfikator tokenu dla subskrypcji dla tego `IDefinitionAppId` obiektu na określoną wartość ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówki** Izolacja. h  
  
 **.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
