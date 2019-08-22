---
title: <nameEntry>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#nameEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/cryptoNameMapping/nameEntry
helpviewer_keywords:
- <nameEntry> element
- nameEntry element
ms.assetid: 7d7535e9-4b4a-4b8c-82e2-e40dff5a7821
ms.openlocfilehash: 9270552245b3867f0f09741ded3f9da6a8b6c135
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664269"
---
# <a name="nameentry-element"></a>\<nameEntry, element >
Mapuje nazwę klasy na przyjazną nazwę algorytmu, która pozwala jednej klasie mieć wiele przyjaznych nazw.  
  
 \<> konfiguracji  
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
|**name**|Atrybut wymagany.<br /><br /> Określa przyjazną nazwę algorytmu, który implementuje Klasa kryptografii.|  
|**class**|Atrybut wymagany.<br /><br /> Określa wartość atrybutu **name** w [ \<elemencie cryptoClass >](cryptoclass-element.md) .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`system.web`|Określa element główny dla sekcji konfiguracji ASP.NET.|  
  
## <a name="remarks"></a>Uwagi  
 Atrybut **name** może być nazwą jednej z klas abstrakcyjnych znalezionych w <xref:System.Security.Cryptography> przestrzeni nazw. Po wywołaniu metody **Create** dla abstrakcyjnej klasy kryptograficznej, nazwa klasy abstrakcyjnej jest przenoszona do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A> metody. Funkcja "nofrom" zwraca wystąpienie typu wskazane przez atrybut **Class** . Jeśli atrybut **name** jest krótką nazwą, taką jak RSA, można użyć tej nazwy podczas wywoływania metody.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu nameEntry >, aby odwoływać się do klasy kryptografii i skonfigurować środowisko uruchomieniowe. Następnie można przekazać ciąg "RSA" do <xref:System.Security.Cryptography.CryptoConfig.CreateFromName%2A?displayProperty=nameWithType> metody i <xref:System.Security.Cryptography.AsymmetricAlgorithm.Create%2A> użyć metody do zwrócenia `MyCryptoRSAClass` obiektu.  
  
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
