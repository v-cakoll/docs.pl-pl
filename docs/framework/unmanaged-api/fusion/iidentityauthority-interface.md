---
title: "IIdentityAuthority — Interfejs"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IIdentityAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IIdentityAuthority
helpviewer_keywords:
- IIdentityAuthority interface [.NET Framework fusion]
ms.assetid: 6277f914-51a8-49be-bec6-52d6d648527d
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 322b15252271472b5bee1dfc6a843079cebbe0b8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority — Interfejs
Zarządza tożsamości klucze obiekty kod.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone [IDefinitionIdentity](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpienia są takie same.|  
|`IIdentityAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) wystąpienia są takie same.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości definicji określonego ciągu są takie same.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości odwołania określonego ciągu są takie same.|  
|`IIdentityAuthority::CreateDefinition`|Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.|  
|`IIdentityAuthority::CreateReference`|Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.|  
|`IIdentityAuthority::DefinitionToText`|Pobiera wersję sformatowanego ciągu określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Wypełnia bufor określony znaków dwubajtowych w ciągu wersji z określonym `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określony `IDefinitionIdentity` i `IReferenceIdentity` wystąpień odwoływać się do tego samego obiektu kodu.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określone ciągi odwoływać się do tego samego obiektu kodu.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Pobiera wskaźnik do nowo utworzony ciąg klucza dla określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Pobiera wskaźnik do nowo utworzony ciąg klucza dla określonego `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Pobiera wartość skrótu dla określonego `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Pobiera wersję sformatowanego ciągu określonego `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Wypełnia bufor określony znaków dwubajtowych w ciągu wersji z określonym `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Pobiera wskaźnika interfejsu do `IDefinitionIdentity` ciąg w formacie wygenerowane z określonego wystąpienia.|  
|`IIdentityAuthority::TextToReference`|Pobiera wskaźnika interfejsu do `IReferenceIdentity` ciąg w formacie wygenerowane z określonego wystąpienia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
