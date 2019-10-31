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
ms.openlocfilehash: 004e4f70e3385e7a71c356cce38e64d0253dcfa4
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127135"
---
# <a name="iappidauthority-interface"></a>IAppIdAuthority — Interfejs
Dostarcza metody, które generują i porównują klucze dla tożsamości i odwołań aplikacji.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|`IAppIdAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone wystąpienia [IDefinitionAppId —](idefinitionappid-interface.md) są równe. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.|  
|`IAppIdAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone wystąpienia [IReferenceAppId —](ireferenceappid-interface.md) są równe. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.|  
|`IAppIdAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone definicje ciągów są równe. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_DEFINITIONS_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.|  
|`IAppIdAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone odwołania do ciągu są równe. Można przekazać wartość flagi IAPPIDAUTHORITY_ARE_REFERENCES_EQUAL_FLAG_IGNORE_VERSION, aby zignorować odpowiednie informacje o wersji.|  
|`IAppIdAuthority::CreateDefinition`|Pobiera wskaźnik interfejsu do nowo wygenerowanego wystąpienia `IDefinitionAppId`, które reprezentuje zestaw w bieżącym zakresie.|  
|`IAppIdAuthority::CreateReference`|Pobiera wskaźnik interfejsu do nowo utworzonego `IReferenceAppId`, który reprezentuje zestaw w bieżącym zakresie.|  
|`IAppIdAuthority::DefinitionToText`|Pobiera wersję ciągu określonego `IDefinitionAppId`przy użyciu określonych wartości flagi.|  
|`IAppIdAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określone `IDefinitionAppId` i `IReferenceAppId` reprezentują ten sam zestaw.|  
|`IAppIdAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określony ciąg definicji i ciąg odwołania reprezentują ten sam zestaw.|  
|`IAppIdAuthority::GenerateDefinitionKey`|Pobiera klucz ciągu, który reprezentuje określone wystąpienie `IDefinitionAppId`.|  
|`IAppIdAuthority::GenerateReferenceKey`|Pobiera klucz ciągu, który reprezentuje określone wystąpienie `IReferenceAppId`.|  
|`IAppIdAuthority::HashDefinition`|Pobiera klucz skrótu dla określonego wystąpienia `IDefinitionAppId`.|  
|`IAppIdAuthority::HashReference`|Pobiera klucz skrótu dla określonego wystąpienia `IReferenceAppId`.|  
|`IAppIdAuthority::ReferenceToText`|Pobiera wersję ciągu określonego `IReferenceAppId`przy użyciu określonych wartości flagi.|  
|`IAppIdAuthority::TextToDefinition`|Pobiera wskaźnik interfejsu do wystąpienia `IDefinitionAppId`, które reprezentuje zestaw, do którego odwołuje się określony klucz ciągu.|  
|`IAppIdAuthority::TextToReference`|Pobiera wskaźnik interfejsu do wystąpienia `IReferenceAppId`, które reprezentuje zestaw, do którego odwołuje się określony klucz ciągu.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Izolacja. h  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
