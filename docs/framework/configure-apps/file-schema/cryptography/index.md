---
title: Schemat ustawień kryptografii
ms.date: 03/30/2017
helpviewer_keywords:
- configuration schema [.NET Framework], cryptography
- elements [.NET Framework], cryptography
- schema configuration settings
- cryptography, settings schema
- cryptography, mapping algorithm names
- configuration sections [.NET Framework]
- configuration settings [.NET Framework], cryptography
ms.assetid: 1f55050a-b2a3-4868-a3c0-da20826150f3
ms.openlocfilehash: a2aa56f8b2a92f906293adfae9d23ed8959336fb
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664295"
---
# <a name="cryptography-settings-schema"></a>Schemat ustawień kryptografii
Schemat ustawień kryptografii zawiera elementy, które określają sposób mapowania przyjaznych nazw algorytmów na klasy implementujące algorytmy kryptografii.  
  
 [ **\<> konfiguracji**](../configuration-element.md)  
  
 [ **\<mscorlib>** ](mscorlib-element-for-cryptography-settings.md)  
  
 [ **\<cryptographySettings>** ](cryptographysettings-element.md)  
  
 [ **\<cryptoNameMapping>** ](cryptonamemapping-element.md)  
  
 [ **\<cryptoClasses>** ](cryptoclasses-element.md)  
  
 [ **\<cryptoClass>** ](cryptoclass-element.md)  
  
 [ **\<nameEntry >** ](nameentry-element.md)  
  
 [ **\<oidMap>** ](oidmap-element.md)  
  
 [ **\<oidEntry>** ](oidentry-element.md)  
  
|Element|Opis|  
|-------------|-----------------|  
|[ **\<cryptoClasses**>](cryptoclasses-element.md)|Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .|  
|[ **\<cryptoClass**>](cryptoclass-element.md)|Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .|  
|[ **\<cryptographySettings**>](cryptographysettings-element.md)|Zawiera ustawienia kryptografii.|  
|[ **\<cryptoNameMapping**>](cryptonamemapping-element.md)|Zawiera mapowania klas do przyjaznych nazw.|  
|[Element > mscorlib dla ustawień kryptografii  **\<** ](mscorlib-element-for-cryptography-settings.md)|Zawiera element **> cryptographySettings.\<**|  
|[ **\<nameEntry >** ](nameentry-element.md)|Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.|  
|[ **\<oidEntry>** ](oidentry-element.md)|Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.|  
|[ **\<oidMap>** ](oidmap-element.md)|Zawiera mapowania identyfikatorów OID ASN. 1 do klas.|  
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
