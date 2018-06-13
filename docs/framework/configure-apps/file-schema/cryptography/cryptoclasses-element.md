---
title: '&lt;cryptoclasses —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 2706d2466bd7139d8a6c20802c32dd19f64abb40
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743007"
---
# <a name="ltcryptoclassesgt-element"></a>&lt;cryptoclasses —&gt; — Element
Zawiera listę klasy kryptografii, które ma mapowania do przyjazną nazwę w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) elementu.  
  
 \<Konfiguracja >  
\<mscorlib >  
\<cryptographysettings — >  
\<cryptonamemapping — >  
\<cryptoclasses — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<cryptoClasses>   
</cryptoClasses>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<cryptoclass — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md)|Zawiera klasy kryptografii, która ma mapowania przyjazną nazwę w  **\<nameentry — >** elementu.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`cryptographySettings`|Zawiera ustawienia szyfrowania.|  
|`cryptoNameMapping`|Zawiera mapowania klasy przyjazne nazwy.|  
|`mscorlib`|Zawiera `cryptographySettings` elementu.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób użycia  **\<cryptoclass — >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe. Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
               <!-- Other cryptography classes go here. -->  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
             <!-- Mappings to other cryptography classes go here. -->  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Security.Cryptography>  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schemat ustawień kryptografii](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)  
 [System.Security.Cryptography.CryptoConfig.CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)  
 [Konfigurowanie klas kryptografii](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
