---
title: <oidEntry>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/mscorlib/cryptographySettings/oidMap/oidEntry
- http://schemas.microsoft.com/.NetConfiguration/v2.0#oidEntry
helpviewer_keywords:
- <oidEntry> element
- oidEntry element
ms.assetid: 22fb88b0-bf27-489c-9ca0-e65950ac136c
ms.openlocfilehash: b1dc4c788576fd3cab55db5255617cc55e68594b
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55259062"
---
# <a name="oidentry-element"></a>\<oidEntry> Element
Mapuje ASN.1 identyfikator obiektu (OID) przyjazną nazwę.  
  
 \<Konfiguracja >  
\<mscorlib>  
\<cryptographySettings>  
\<oidMap>  
\<oidEntry>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**OID**|Atrybut wymagany.<br /><br /> Określa identyfikator OID ASN.1 odpowiadający algorytm implementowane przez klasy.|  
|**Nazwa**|Atrybut wymagany.<br /><br /> Określa wartość dla **nazwa** atrybutu w [ \<nameentry — >](../../../../../docs/framework/configure-apps/file-schema/cryptography/nameentry-element.md) tagu.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`cryptographySettings`|Zawiera ustawienia szyfrowania.|  
|`mscorlib`|Zawiera `cryptographySettings` elementu.|  
|`oidMap`|Zawiera mapowania identyfikatora (OID) obiektów ASN.1 do klas.|  
  
## <a name="remarks"></a>Uwagi  
 Identyfikatory obiektów ASN.1 zidentyfikować algorytmów w niektórych formatach kryptograficznych. Mapowanie identyfikatorów obiektów na przyjazne nazwy dla algorytmów, który chcesz zidentyfikować.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak używać  **\<oidentry — >** element do mapy identyfikator obiektu algorytmu wyznaczania wartości skrótu RIPEMD 160 implementacji tego algorytmu wyznaczania wartości skrótu.  
  
```xml  
<configuration>  
   <mscorlib>  
      <cryptographySettings>  
         <cryptoNameMapping>  
            <cryptoClasses>  
               <cryptoClass   MyCrypto="MyCryptoClass, MyAssembly  
                  Culture=neutral, PublicKeyToken=a5d015c7d5a0b012,  
                  Version=1.0.0.0"/>  
            </cryptoClasses>  
            <nameEntry name="RIPEMD-160" class="MyCrypto"/>  
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
- [Konfigurowanie klas kryptografii](../../../../../docs/framework/configure-apps/configure-cryptography-classes.md)
- [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](../../../../../docs/framework/configure-apps/map-object-identifiers-to-cryptography-algorithms.md)
