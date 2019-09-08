---
title: Interfejsy łączenia
ms.date: 03/30/2017
helpviewer_keywords:
- interfaces [.NET Framework fusion]
- fusion interfaces [.NET Framework]
- unmanaged interfaces [.NET Framework], fusion
ms.assetid: e2cf98b7-40c1-4f74-86c7-8a76dd9da677
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1605605f8510f7ccf5f0bbf2f3f6b09050a16025
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795301"
---
# <a name="fusion-interfaces"></a>Interfejsy łączenia
W tej sekcji opisano niezarządzane interfejsy, które są używane przez interfejs API Fusion do uzyskiwania dostępu do właściwości zasobów aplikacji i lokalizowania odpowiednich wersji tych zasobów dla aplikacji.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [IAppIdAuthority, interfejs](iappidauthority-interface.md)  
 Dostarcza metody, które generują i porównują klucze dla tożsamości i odwołań aplikacji.  
  
 [IAssemblyCache, interfejs](iassemblycache-interface.md)  
 Przedstawia reprezentację globalnej pamięci podręcznej zestawów.  
  
 [IAssemblyCacheItem, interfejs](iassemblycacheitem-interface.md)  
 Reprezentuje pojedynczy zestaw w globalnej pamięci podręcznej zestawów.  
  
 [IAssemblyEnum, interfejs](iassemblyenum-interface.md)  
 Reprezentuje moduł wyliczający dla tablicy `IAssemblyName` obiektów.  
  
 [IAssemblyName, interfejs](iassemblyname-interface.md)  
 Zapewnia metody opisujące unikatową tożsamość zestawu i pracę z nim.  
  
 [IDefinitionAppId, interfejs](idefinitionappid-interface.md)  
 Reprezentuje unikatowy identyfikator kodu, który definiuje aplikację w bieżącym zakresie.  
  
 [IDefinitionIdentity, interfejs](idefinitionidentity-interface.md)  
 Reprezentuje unikatowy podpis kodu, który definiuje aplikację w bieżącym zakresie.  
  
 [IEnumDefinitionIdentity, interfejs](ienumdefinitionidentity-interface.md)  
 Służy jako moduł wyliczający dla kolekcji `IDefinitionIdentity` obiektów.  
  
 [IEnumIDENTITY_ATTRIBUTE, interfejs](ienumidentity-attribute-interface.md)  
 Służy jako moduł wyliczający dla atrybutów obiektu kodu w bieżącym zakresie.  
  
 [IEnumReferenceIdentity, interfejs](ienumreferenceidentity-interface.md)  
 Służy jako moduł wyliczający dla kolekcji `IReferenceIdentity` obiektów.  
  
 [IIdentityAuthority, interfejs](iidentityauthority-interface.md)  
 Zarządza kluczami tożsamości dla obiektów kodu.  
  
 [IInstallReferenceEnum, interfejs](iinstallreferenceenum-interface.md)  
 Reprezentuje moduł wyliczający dla zestawów, do których istnieją odwołania zainstalowane w globalnej pamięci podręcznej zestawów.  
  
 [IInstallReferenceItem, interfejs](iinstallreferenceitem-interface.md)  
 Reprezentuje element zainstalowany w globalnej pamięci podręcznej zestawów.  
  
 [IReferenceAppId, interfejs](ireferenceappid-interface.md)  
 Reprezentuje odwołanie do unikatowego identyfikatora aplikacji w bieżącym zakresie.  
  
 [IReferenceIdentity, interfejs](ireferenceidentity-interface.md)  
 Reprezentuje odwołanie do unikatowego podpisu obiektu kodu.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Reflection>  
  
 <xref:System.Reflection.Emit>  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Łączenie statycznych funkcji globalnych](fusion-global-static-functions.md)  
  
 [Wyliczenia łączenia](fusion-enumerations.md)  
  
 [Łączenie — struktury](fusion-structures.md)
