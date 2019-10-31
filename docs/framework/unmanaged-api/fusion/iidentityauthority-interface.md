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
ms.openlocfilehash: 3e2d2335e37ced9139ea44092f10b19566894681
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127096"
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
|`IIdentityAuthority::CreateDefinition`|Pobiera wskaźnik do nowego wystąpienia `IDefinitionIdentity`, które reprezentuje obiekt kodu w bieżącym zakresie.|
|`IIdentityAuthority::CreateReference`|Pobiera wskaźnik do nowego wystąpienia `IReferenceIdentity`, które reprezentuje obiekt kodu w bieżącym zakresie.|
|`IIdentityAuthority::DefinitionToText`|Pobiera sformatowaną wersję ciągu określonego `IDefinitionIdentity`.|
|`IIdentityAuthority::DefinitionToTextBuffer`|Wypełnia określony bufor szerokich znaków za pomocą wersji ciągu określonego `IDefinitionIdentity`.|
|`IIdentityAuthority::DoesDefinitionMatchReference`|Pobiera wartość wskazującą, czy określone wystąpienia `IDefinitionIdentity` i `IReferenceIdentity` odwołują się do tego samego obiektu kodu.|
|`IIdentityAuthority::DoesTextualDefinitionMatchTextualReference`|Pobiera wartość wskazującą, czy określone ciągi odwołują się do tego samego obiektu kodu.|
|`IIdentityAuthority::GenerateDefinitionKey`|Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IDefinitionIdentity`.|
|`IIdentityAuthority::GenerateReferenceKey`|Pobiera wskaźnik do nowo utworzonego klucza ciągu dla określonego `IReferenceIdentity`.|
|`IIdentityAuthority::HashDefinition`|Pobiera wartość skrótu dla określonego `IDefinitionIdentity`.|
|`IIdentityAuthority::HashReference`|Pobiera wartość skrótu dla określonego `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToText`|Pobiera sformatowaną wersję ciągu określonego `IReferenceIdentity`.|
|`IIdentityAuthority::ReferenceToTextBuffer`|Wypełnia określony bufor szerokich znaków za pomocą wersji ciągu określonego `IReferenceIdentity`.|
|`IIdentityAuthority::TextToDefinition`|Pobiera wskaźnik interfejsu do wystąpienia `IDefinitionIdentity` wygenerowanego na podstawie określonego sformatowanego ciągu.|
|`IIdentityAuthority::TextToReference`|Pobiera wskaźnik interfejsu do wystąpienia `IReferenceIdentity` wygenerowanego na podstawie określonego sformatowanego ciągu.|

## <a name="requirements"></a>Wymagania

**Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).

**Nagłówek:** Izolacja. h

**Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]

## <a name="see-also"></a>Zobacz także

- [Interfejsy łączenia](fusion-interfaces.md)
