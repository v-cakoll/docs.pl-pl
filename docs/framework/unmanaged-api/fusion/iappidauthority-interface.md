---
title: IAppIdAuthority — Interfejs
ms.date: 03/30/2017
api_name:
- IAppIdAuthority
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IAppIdAuthority
helpviewer_keywords:
- IAppIdAuthority interface [.NET Framework fusion]
ms.assetid: ec354fa1-1efd-41b0-bc43-b90597b6e253
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 724ee01e91f1e9f4e34d2262610152a977ed4f53
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61697579"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority — Interfejs
Udostępnia metody, generujących i klucze dla tożsamości aplikacji i odwołania do porównania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone [idefinitionappid —](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) wystąpień są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.|  
|`IAppIdAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone [ireferenceappid —](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) wystąpień są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwie definicje określonego ciągu są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwa odwołania określonego ciągu są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION ignorowanie informacjami o odpowiedniej wersji.|  
|`IAppIdAuthority::CreateDefinition`|Pobiera wskaźnik interfejsu do nowo wygenerowane `IDefinitionAppId` wystąpienia, która reprezentuje zestaw w bieżącym zakresie.|  
|`IAppIdAuthority::CreateReference`|Pobiera wskaźnik interfejsu do nowo utworzonego `IReferenceAppId` reprezentujący zestaw w bieżącym zakresie.|  
|`IAppIdAuthority::DefinitionToText`|Pobiera wersję ciągu określonego `IDefinitionAppId`, przy użyciu flagi określonej wartości.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określony `IDefinitionAppId` i `IReferenceAppId` reprezentują tego samego zestawu.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy podana definicja ciągu i ciąg odwołania reprezentują tego samego zestawu.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Pobiera klucz ciąg, który reprezentuje określony `IDefinitionAppId` wystąpienia.|  
|`IAppIdAuthority::GenerateReferenceKey`|Pobiera klucz ciąg, który reprezentuje określony `IReferenceAppId` wystąpienia.|  
|`IAppIdAuthority::HashDefinition`|Pobiera klucz wyznaczania wartości skrótu dla określonego `IDefinitionAppId` wystąpienia.|  
|`IAppIdAuthority::HashReference`|Pobiera klucz wyznaczania wartości skrótu dla określonego `IReferenceAppId` wystąpienia.|  
|`IAppIdAuthority::ReferenceToText`|Pobiera wersję ciągu określonego `IReferenceAppId`, przy użyciu flagi określonej wartości.|  
|`IAppIdAuthority::TextToDefinition`|Pobiera wskaźnik interfejsu do `IDefinitionAppId` wystąpienia, która reprezentuje zestaw odwołania za pomocą klucza określonego ciągu.|  
|`IAppIdAuthority::TextToReference`|Pobiera wskaźnik interfejsu do `IReferenceAppId` wystąpienia, która reprezentuje zestaw odwołania za pomocą klucza określonego ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
