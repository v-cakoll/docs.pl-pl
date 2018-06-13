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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: b7f41bc477f8d8095bf73859c02b7e2fc2443c14
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742877"
---
# <a name="cryptography-settings-schema"></a>Schemat ustawień kryptografii
Schemat ustawień kryptografii zawiera elementy, które określają sposób odwzorowywania algorytm przyjaznej nazwy klasy, które implementują algorytmów kryptograficznych.  
  
 [**\<Konfiguracja >**](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [**\<mscorlib >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)  
  
 [**\<cryptographysettings — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)  
  
 [**\<cryptonamemapping — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)  
  
 [**\<cryptoclasses — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)  
  
 [**\<cryptoclass — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)  
  
 [**\<nameentry — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)  
  
 [**\<oidmap — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)  
  
 [**\<oidentry — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)  
  
|Element|Opis|  
|-------------|-----------------|  
|[**\<cryptoclasses —**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclasses-element.md)|Zawiera listę klasy kryptografii, które ma mapowania do przyjazną nazwę w  **\<nameentry — >** elementu.|  
|[**\<cryptoclass —**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Zawiera klasy kryptografii, która ma mapowania przyjazną nazwę w  **\<nameentry — >** elementu.|  
|[**\<cryptographysettings —**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptographysettings-element.md)|Zawiera ustawienia szyfrowania.|  
|[**\<cryptonamemapping —**>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Zawiera mapowania klasy przyjazne nazwy.|  
|[**\<mscorlib >** element ustawień kryptografii](../../../../../docs/framework/configure-apps/file-schema/cryptography/mscorlib-element-for-cryptography-settings.md)|Zawiera  **\<cryptographysettings — >** elementu.|  
|[**\<nameentry — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md)|Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.|  
|[**\<oidentry — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidentry-element.md)|Mapuje ASN.1 identyfikatora obiektu (OID) przyjazną nazwę.|  
|[**\<oidmap — >**](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|Zawiera identyfikator OID ASN.1 mapowania do klasy.|  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
