---
title: <cryptoClasses>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/cryptoClasses
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoClasses
helpviewer_keywords:
- <cryptoClasses> element
- cryptoClasses element
ms.assetid: 290d5f96-946d-4f02-babb-1d31ec0b8295
ms.openlocfilehash: 87e64ecd79ebc54a669d33550790781c87b5917c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921132"
---
# <a name="cryptoclasses-element"></a>\<cryptoClasses> Element
Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w [ \<elemencie nameEntry >](nameentry-element.md) .  
  
 \<> konfiguracji  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<cryptoClasses>  
  
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
|[\<cryptoClass>](cryptoclass-element.md)|Zawiera klasę kryptografii, która ma mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`cryptographySettings`|Zawiera ustawienia kryptografii.|  
|`cryptoNameMapping`|Zawiera mapowania klas do przyjaznych nazw.|  
|`mscorlib`|`cryptographySettings` Zawiera element.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu cryptoClass >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe. Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Security.Cryptography>
- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kryptografii](index.md)
- [Usługi kryptograficzne](../../../../standard/security/cryptographic-services.md)
- [System.Security.Cryptography.CryptoConfig.CreateFromName](Overload:System.Security.Cryptography.CryptoConfig.CreateFromName)
- [Konfigurowanie klas kryptografii](../../configure-cryptography-classes.md)
