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
ms.openlocfilehash: 2735355097a1f3f581b3a4bc74f08d8f2ebf3bd8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430383"
---
# <a name="idefinitionappid-interface"></a>IDefinitionAppId — Interfejs
Reprezentuje unikatowy identyfikator dla kodu, który definiuje aplikacji w bieżącym zakresie.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IDefinitionAppId::get_Codebase`|Pobiera ciąg formatowania, który reprezentuje kod w tym `IDefinitionAppId` obiektu.|  
|`IDefinitionAppId::put_Codebase`|Ustawia kod to `IDefinitionAppId` wartość ciągu sformatowaną jak określony obiekt.|  
|`IDefinitionAppId::EnumAppPath`|Pobiera wskaźnika interfejsu do [IEnumDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/ienumdefinitionidentity-interface.md) obiekt, który zawiera zestawy w ścieżce bieżącej aplikacji.|  
|`IDefinitionAppId::SetAppPath`|Ustawia ścieżkę aplikacji dla zestawu w bieżącym zakresie wartości odwołuje się określony [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) obiektu.|  
|`IDefinitionAppId::get_SubscriptionId`|Pobiera wskaźnik do reprezentację ciągu identyfikatora tokenu dla tej subskrypcji `IDefinitionAppId` obiektu.|  
|`IDefinitionAppId::put_SubscriptionId`|Ustawia token identyfikator subskrypcji do tego `IDefinitionAppId` obiektu określona wartość ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
