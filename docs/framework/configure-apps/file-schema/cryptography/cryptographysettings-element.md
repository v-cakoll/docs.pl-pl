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
ms.openlocfilehash: 572a5856c9f92f105e727df1ecd8eb2e0a92fc09
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664280"
---
# <a name="cryptographysettings-element"></a>\<cryptographySettings> Element
Zawiera ustawienia kryptografii.  
  
 \<> konfiguracji  
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
|[\<cryptoNameMapping>](cryptonamemapping-element.md)|Zawiera mapowania klas do przyjaznych nazw.|  
|[\<oidMap>](oidmap-element.md)|Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`mscorlib`|`cryptographySettings` Zawiera element.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu cryptographySettings >, aby zawierał mapowania nazw kryptograficznych i mapowania identyfikatorów OID. Ten przykład umożliwia skonfigurowanie środowiska uruchomieniowego <xref:System.Security.Cryptography.HashAlgorithm.Create%2A?displayProperty=nameWithType> w taki `MyHashClass` sposób, aby `MyCryptoClass` zwracało obiekt i klasę do 1.3.36.2.1 identyfikatora obiektu.  
  
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

- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kryptografii](index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
