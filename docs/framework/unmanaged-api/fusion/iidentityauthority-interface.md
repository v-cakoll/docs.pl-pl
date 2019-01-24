---
title: IIdentityAuthority — Interfejs
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ab8965ca5d6c9c96cea5f5b351547ce2d4dfacc7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54546283"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority — Interfejs
Zarządza kluczy tożsamości dla obiektów kodu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IIdentityAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone [idefinitionidentity —](../../../../docs/framework/unmanaged-api/fusion/idefinitionidentity-interface.md) wystąpień są takie same.|  
|`IIdentityAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone [ireferenceidentity —](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) wystąpień są takie same.|  
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości definicji określonego ciągu są takie same.|  
|`IIdentityAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwa oświadczenia tożsamości odwołanie do określonego ciągu są takie same.|  
|`IIdentityAuthority::CreateDefinition`|Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.|  
|`IIdentityAuthority::CreateReference`|Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, który reprezentuje obiekt kodu w bieżącym zakresie.|  
|`IIdentityAuthority::DefinitionToText`|Pobiera wersję sformatowany ciąg, z określonym `IDefinitionIdentity`.|  
|`IIdentityAuthority::DefinitionToTextBuffer`|Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określony `IDefinitionIdentity` i `IReferenceIdentity` wystąpień odnoszą się do tego samego obiektu kodu.|  
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określone ciągi odnoszą się do tego samego obiektu kodu.|  
|`IIdentityAuthority::GenerateDefinitionKey`|Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::GenerateReferenceKey`|Pobiera wskaźnik do ciągu nowo utworzony klucz dla określonego `IReferenceIdentity`.|  
|`IIdentityAuthority::HashDefinition`|Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.|  
|`IIdentityAuthority::HashReference`|Pobiera wartość skrótu dla określonego `IreferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToText`|Pobiera wersję sformatowany ciąg, z określonym `IReferenceIdentity`.|  
|`IIdentityAuthority::ReferenceToTextBuffer`|Wypełnia buforu określonego znaku dwubajtowego ciągu wersję określonego `IReferenceIdentity`.|  
|`IIdentityAuthority::TextToDefinition`|Pobiera wskaźnik interfejsu do `IDefinitionIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.|  
|`IIdentityAuthority::TextToReference`|Pobiera wskaźnik interfejsu do `IReferenceIdentity` ciąg w formacie wygenerowany na podstawie określonego wystąpienia.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
