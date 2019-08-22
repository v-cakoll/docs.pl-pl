---
title: <mscorlib>, element ustawień kryptografii
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mscorlib
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib
helpviewer_keywords:
- mscorlib element
- <mscorlib> element
ms.assetid: d549668f-31f1-4b92-8021-a9135c09ca3c
ms.openlocfilehash: 312db8ea5ae4b66fd00faad1b788eac0356aeaa7
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659600"
---
# <a name="mscorlib-element-for-cryptography-settings"></a>\<Element > mscorlib dla ustawień kryptografii
Zawiera [element > cryptographySettings.\<](cryptographysettings-element.md)  
  
 \<> konfiguracji  
\<mscorlib>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
      <mscorlib>   
</mscorlib>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`cryptographySettings`|Zawiera ustawienia kryptografii.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu > mscorlib do odwoływania się do klasy kryptografii i konfigurowania środowiska uruchomieniowego. Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.  
  
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

- <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A>
- <xref:System.Security.Cryptography>
- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kryptografii](index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
- [Konfigurowanie klas kryptografii](../../configure-cryptography-classes.md)
