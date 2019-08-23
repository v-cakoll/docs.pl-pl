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
ms.openlocfilehash: cbdf6150010ca2dace3f0610d9caa90c2bf52746
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921057"
---
# <a name="oidentry-element"></a>\<oidEntry, element >
Mapuje identyfikator obiektu ASN. 1 (OID) na przyjazną nazwę.  
  
 \<> konfiguracji  
\<mscorlib>  
\<cryptographySettings>  
\<oidMap>  
\<oidEntry >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<oidEntry OID="object identifier number" name="friendly name" />  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|**OID**|Atrybut wymagany.<br /><br /> Określa identyfikator OID ASN. 1 odpowiadający algorytmowi zaimplementowanemu przez klasę.|  
|**name**|Atrybut wymagany.<br /><br /> Określa wartość atrybutu **name** w [ \<tagu > nameEntry](nameentry-element.md) .|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|`configuration`|Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework.|  
|`cryptographySettings`|Zawiera ustawienia kryptografii.|  
|`mscorlib`|`cryptographySettings` Zawiera element.|  
|`oidMap`|Zawiera mapowania identyfikatorów obiektów ASN. 1 (OID) do klas.|  
  
## <a name="remarks"></a>Uwagi  
 Identyfikatory obiektu ASN. 1 identyfikują algorytmy w niektórych formatach kryptograficznych. Mapuj identyfikatory obiektów na przyjazne nazwy dla algorytmów, które chcesz zidentyfikować.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje,  **\<** jak używać elementu oidEntry > do mapowania identyfikatora obiektu dla algorytmu wyznaczania wartości skrótu RIPEMD-160 do implementacji algorytmu wyznaczania wartości skrótu.  
  
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

- [Schemat pliku konfiguracji](../index.md)
- [Schemat ustawień kryptografii](index.md)
- [Usługi kryptograficzne](../../../../standard/security/cryptographic-services.md)
- [Konfigurowanie klas kryptografii](../../configure-cryptography-classes.md)
- [Mapowanie identyfikatorów obiektów na algorytmy kryptografii](../../map-object-identifiers-to-cryptography-algorithms.md)
