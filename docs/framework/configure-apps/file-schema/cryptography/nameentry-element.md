---
title: '&lt;nameentry —&gt; — Element'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1bffb72e7c68d10e2c0edd5ec3cb9bcff10cbc0a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="ltnameentrygt-element"></a>&lt;nameentry —&gt; — Element
Mapuje nazwę klasy na nazwę algorytmu przyjazną, która umożliwia jedną klasę do mają wiele przyjaznej nazwy.  
  
 \<Konfiguracja >  
\<mscorlib >  
\<cryptographysettings — >  
\<cryptonamemapping — >  
\<nameentry — >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**Nazwa**|Atrybut wymagany.<br /><br /> Określa przyjazną nazwę algorytmu, który implementuje klasy kryptografii.|  
|**class**|Atrybut wymagany.<br /><br /> Określa wartość **nazwa** atrybutu w [ \<cryptoclass — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.web`|Określa element root dla sekcji konfiguracji ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 **Nazwa** atrybut może być nazwę jednej z klas abstrakcyjnych w <xref:System.Security.Cryptography> przestrzeni nazw. Podczas wywoływania **Utwórz** metody dla klasy abstrakcyjnej kryptografii, nazwa klasy abstrakcyjnej jest przekazywany do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody. **CreateFromName** zwraca wystąpienia typu oznaczonego **klasy** atrybutu. Jeśli **nazwa** atrybut jest krótką nazwę, takich jak RSA, można użyć tej nazwy podczas wywoływania **CreateFromName** metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie  **\<nameentry — >** element odwołuje się do klasy kryptografii i skonfigurować środowisko uruchomieniowe. Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> — metoda i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCryptoRSA="MyCryptoRSAClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RSA" class="MyCryptoRSA"/>  
            <nameEntry name="System.Security.Cryptography.AsymmetricAlgorithm"  
                       class="MyCryptoRSA"/>  
         </cryptoNameMapping>  
      </cryptographySettings>  
   </mscorlib>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Schemat ustawień kryptografii](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)  
 [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)  
 [Konfigurowanie klas kryptografii](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
