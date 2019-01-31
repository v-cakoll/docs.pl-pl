---
title: <cryptographySettings>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptographySettings
helpviewer_keywords:
- cryptographySettings element
- <cryptographySettings> element
ms.assetid: 6201b7da-bcb7-49f7-b9f5-ba1fe05573b9
ms.openlocfilehash: 11f07bbf5de04edc98a5a5bc0ba07f1629763a9f
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55258711"
---
# <a name="cryptographysettings-element"></a>\<cryptographySettings> Element
Zawiera ustawienia szyfrowania.  
  
 \<Konfiguracja >  
\<mscorlib>  
\<cryptographySettings>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <cryptographySettings>   
</cryptographySettings>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cryptoNameMapping>](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptonamemapping-element.md)|Zawiera mapowania klasy przyjazne nazwy.|  
|[\<oidMap>](../../../../../docs/framework/configure-apps/file-schema/cryptography/oidmap-element.md)|Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`mscorlib`|Zawiera `cryptographySettings` elementu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje jak używać  **\<cryptographysettings — >** element zawiera mapowania identyfikatora OID i mapowań nazw kryptografii. Ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego, aby <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> zwraca `MyHashClass` obiektu i `MyCryptoClass` klasy mapuje do identyfikatora obiektu 1.3.36.2.1.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyHash="MyHashClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="System.Security.Cryptography.HashAlgorithm"  
                       class="MyHash"/>  
         </cryptoNameMapping>  
         <oidMap>  
            <oidEntry OID="1.3.36.3.2.1"   name="MyCryptoClass"/>  
         </oidMap>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Schemat ustawień kryptografii](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
