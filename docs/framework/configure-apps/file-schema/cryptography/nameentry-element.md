---
title: <nameEntry> Element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 97521ba9073820beeea62f5fc7cab480b5422fb0
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225329"
---
# <a name="nameentry-element"></a>\<nameEntry> Element
Mapuje nazwę klasy na nazwę algorytmu przyjazna, która umożliwia jednej klasy mają wiele przyjazne nazwy.  
  
 \<Konfiguracja >  
\<mscorlib>  
\<cryptographySettings>  
\<cryptoNameMapping>  
\<nameEntry>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<nameEntry name="friendly name" Class="class name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**nazwa**|Atrybut wymagany.<br /><br /> Określa przyjazną nazwę algorytmu, który implementuje klasa kryptografii.|  
|**class**|Atrybut wymagany.<br /><br /> Określa wartość dla **nazwa** atrybutu w [ \<cryptoclass — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/cryptoclass-element.md) elementu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.web`|Określa element root dla sekcji konfiguracyjnej platformy ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 **Nazwa** atrybut może być nazwą jednego z klasy abstrakcyjnej, znalezione w <xref:System.Security.Cryptography> przestrzeni nazw. Gdy wywołujesz **Utwórz** metody na klasy kryptografii abstrakcyjne, nazwa klasy abstrakcyjnej jest przekazywany do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody. **CreateFromName** Zwraca wystąpienie typu wskazywanym przez **klasy** atrybutu. Jeśli **nazwa** atrybut jest krótką nazwę, takich jak RSA, można użyć tej nazwy, podczas wywoływania **CreateFromName** metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać  **\<nameentry — >** element odwołuje się do klasy kryptografii i konfigurowanie środowiska uruchomieniowego. Ciąg "RSA" można następnie przekazać do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i użyj <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> metodę, aby zwrócić `MyCryptoRSAClass` obiektu.  
  
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

- [Schemat pliku konfiguracji](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Schemat ustawień kryptografii](../../../../../docs/framework/configure-apps/file-schema/cryptography/index.md)
- [Usługi kryptograficzne](../../../../../docs/standard/security/cryptographic-services.md)
- [Konfigurowanie klasy kryptografii](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
