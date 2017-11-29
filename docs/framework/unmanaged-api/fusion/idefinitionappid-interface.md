---
title: "IDefinitionAppId — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IDefinitionAppId
api_location: fusion.dll
api_type: COM
f1_keywords: IDefinitionAppId
helpviewer_keywords: IDefinitionAppId interface [.NET Framework fusion]
ms.assetid: e72f2550-bdec-4a20-a2f4-2e14847266c1
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 382c82ff773d0ab1c046fc131fa87a4f74d19ea6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
