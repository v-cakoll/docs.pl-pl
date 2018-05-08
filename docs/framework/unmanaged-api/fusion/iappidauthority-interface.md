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
ms.openlocfilehash: 819afec2c448e5f396ab54e2dde00c01da310b12
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority — Interfejs
Udostępnia metody, które Generowanie i klucze dla tożsamości aplikacji i odwołania do porównania.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone [IDefinitionAppId](../../../../docs/framework/unmanaged-api/fusion/idefinitionappid-interface.md) wystąpienia są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.|  
|`IAppIdAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone [IReferenceAppId](../../../../docs/framework/unmanaged-api/fusion/ireferenceappid-interface.md) wystąpienia są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwie definicje określonego ciągu są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwa odwołania określonego ciągu są takie same. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION zignorowanie informacji o ich odpowiedniej wersji.|  
|`IAppIdAuthority::CreateDefinition`|Pobiera wskaźnika interfejsu do nowo utworzonego `IDefinitionAppId` wystąpienia, który reprezentuje zestaw w bieżącym zakresie.|  
|`IAppIdAuthority::CreateReference`|Pobiera wskaźnika interfejsu, aby nowo utworzony `IReferenceAppId` reprezentujący zestawu w bieżącym zakresie.|  
|`IAppIdAuthority::DefinitionToText`|Pobiera wersję ciągu określonego `IDefinitionAppId`, przy użyciu flagi określonej wartości.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określony `IDefinitionAppId` i `IReferenceAppId` reprezentują tego samego zestawu.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określona definicja ciągu i ciąg odwołania reprezentują tego samego zestawu.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Pobiera klucz ciąg reprezentujący określonego `IDefinitionAppId` wystąpienia.|  
|`IAppIdAuthority::GenerateReferenceKey`|Pobiera klucz ciąg reprezentujący określonego `IReferenceAppId` wystąpienia.|  
|`IAppIdAuthority::HashDefinition`|Pobiera klucz wyznaczania wartości skrótu dla określonego `IDefinitionAppId` wystąpienia.|  
|`IAppIdAuthority::HashReference`|Pobiera klucz wyznaczania wartości skrótu dla określonego `IReferenceAppId` wystąpienia.|  
|`IAppIdAuthority::ReferenceToText`|Pobiera wersję ciągu określonego `IReferenceAppId`, przy użyciu flagi określonej wartości.|  
|`IAppIdAuthority::TextToDefinition`|Pobiera wskaźnika interfejsu do `IDefinitionAppId` wystąpienia, reprezentujący zestaw odwołuje się określony ciąg klucza.|  
|`IAppIdAuthority::TextToReference`|Pobiera wskaźnika interfejsu do `IReferenceAppId` wystąpienia, reprezentujący zestaw odwołuje się określony ciąg klucza.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** Isolation.h  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy łączenia](../../../../docs/framework/unmanaged-api/fusion/fusion-interfaces.md)
