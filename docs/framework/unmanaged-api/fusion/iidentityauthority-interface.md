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
ms.openlocfilehash: 7421e0d0e1a1f0e1a5fbe0d0eb7d5a0ab2a48b9a
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70796423"
---
# <a name="iidentityauthority-interface"></a>IIdentityAuthority — Interfejs

Zarządza kluczami tożsamości dla obiektów kodu.

## <a name="methods"></a>Metody

|Metoda|Opis|
|------------|-----------------|
|`IIdentityAuthority::AreDefinitionsEqual`|Pobiera wartość wskazującą, czy dwa określone wystąpienia [IDefinitionIdentity —](idefinitionidentity-interface.md) są równe.|
|`IIdentityAuthority::AreReferencesEqual`|Pobiera wartość wskazującą, czy dwa określone wystąpienia [IReferenceIdentity —](ireferenceidentity-interface.md) są równe.|
|`IIdentityAuthority::AreTextualDefinitionsEqual`|Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości definicji ciągu są równe.|
|`IIdentityAuthority::AreTextualReferencesEqual`|Pobiera wartość wskazującą, czy dwie określone reprezentacje tożsamości odwołania do ciągu są równe.|
|`IIdentityAuthority::CreateDefinition`|Pobiera wskaźnik do nowego `IDefinitionIdentity` wystąpienia, które reprezentuje obiekt kodu w bieżącym zakresie.|
|`IIdentityAuthority::CreateReference`|Pobiera wskaźnik do nowego `IReferenceIdentity` wystąpienia, które reprezentuje obiekt kodu w bieżącym zakresie.|
|`IIdentityAuthority::DefinitionToText`|Pobiera sformatowaną wersję ciągu określonego `IDefinitionIdentity`.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Wypełnia określony bufor znaków wide z określoną `IDefinitionIdentity`wersją ciągu.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określone `IDefinitionIdentity` i `IReferenceIdentity` wystąpienia odwołują się do tego samego obiektu kodu.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określone ciągi odwołują się do tego samego obiektu kodu.|
|`IIdentityAuthority::GenerateDefinitionKey`|Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IDefinitionIdentity`elementu.|
|`IIdentityAuthority::GenerateReferenceKey`|Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IReferenceIdentity`elementu.|
|`IIdentityAuthority::HashDefinition`|Pobiera wartość skrótu dla określonego `IDefinitionIdentity`elementu.|
|`IIdentityAuthority::HashReference`|Pobiera wartość skrótu dla określonego `IReferenceIdentity`elementu.|
|`IIdentityAuthority::ReferenceToText`|Pobiera sformatowaną wersję ciągu określonego `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Wypełnia określony bufor znaków wide z określoną `IReferenceIdentity`wersją ciągu.|
|`IIdentityAuthority::TextToDefinition`|Pobiera wskaźnik interfejsu do `IDefinitionIdentity` wystąpienia wygenerowanego na podstawie określonego sformatowanego ciągu.|
|`IIdentityAuthority::TextToReference`|Pobiera wskaźnik interfejsu do `IReferenceIdentity` wystąpienia wygenerowanego na podstawie określonego sformatowanego ciągu.|

## <a name="requirements"></a>Wymagania

**Poszczególnych** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówki** Izolacja. h

**.NET Framework wersje:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
