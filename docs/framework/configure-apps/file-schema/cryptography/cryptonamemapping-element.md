---
title: <cryptoNameMapping>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#cryptoNameMapping
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping
helpviewer_keywords:
- <cryptoNameMapping> element
- cryptoNameMapping element
ms.assetid: c59c9494-149b-4ce6-b38d-371f896ae85c
ms.openlocfilehash: c2652ac73c1d55f09a1f8511603003dc6d7291f9
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659645"
---
# <a name="cryptonamemapping-element"></a>\<cryptoNameMapping> Element
Zawiera mapowania klas do przyjaznych nazw.  
  
 \<> konfiguracji  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <cryptoNameMapping>   
</cryptoNameMapping>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`cryptoClasses`|Zawiera listę klas kryptograficznych, które mają mapowanie do przyjaznej nazwy w  **\<elemencie nameEntry >** .|  
|`nameEntry`|Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`cryptographySettings`|Zawiera ustawienia kryptografii.|  
|`cryptoNameMapping`|Zawiera mapowania klas do przyjaznych nazw.|  
|`mscorlib`|Zawiera element > cryptographySettings. \<|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu cryptoNameMapping >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe. Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kryptografii](index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
- [Konfigurowanie klas kryptografii](../../configure-cryptography-classes.md)
