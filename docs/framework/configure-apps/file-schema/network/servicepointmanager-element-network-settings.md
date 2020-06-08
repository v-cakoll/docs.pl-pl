---
title: <servicePointManager>, element (ustawienia sieci)
description: <servicePointManager>Element ustawień sieciowych konfiguruje połączenia z opcjami zasobów sieciowych w .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504527"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager>, element (ustawienia sieci)
Konfiguruje połączenia z zasobami sieciowymi.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

## <a name="syntax"></a>Składnia  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`checkCertificateName`|Określa, czy przed użyciem certyfikatu system powinien sprawdzić, czy nazwa certyfikatu jest zgodna z nazwą hosta serwera. Wartość domyślna to `true`.|  
|`checkCertificateRevocationList`|Określa, czy system powinien sprawdzić, czy certyfikat został odwołany przed użyciem certyfikatu. Wartość domyślna to `false`.|  
|`dnsRefreshTimeout`|Określa, jak długo w milisekundach jest buforowanych rozwiązań usługi nazw domen (DNS) w połączeniu z opcją działania okrężnego systemu DNS. Wartość domyślna to 120 000 milisekund (dwie minuty).|  
|`enableDnsRoundRobin`|Określa, czy rozwiązania DNS nazw hostów z wieloma adresami IP (Internet Protocol) zwracają wszystkie adresy, czy tylko pierwszy. Wartość domyślna to `false`.|  
|`encryptionPolicy`|Określa zasady szyfrowania stosowane do sesji SSL/TLS w <xref:System.Net.ServicePointManager> wystąpieniu. Możliwe wartości są równoważne z wartościami <xref:System.Net.Security.EncryptionPolicy> wyliczenia. Użycie <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagane, gdy zasady szyfrowania są ustawione na `NoEncryption` . Wartość domyślna to `RequireEncryption`.|  
|`expect100Continue`|Określa, czy metody POST powinny oczekiwać `100-continue` odpowiedzi z serwera. Wartość domyślna to `true`.|  
|`useNagleAlgorithm`|Określa, czy połączenia kontrolowane przez Menedżera punktów usług używają algorytmu nagle. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Postaci**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schemat ustawień sieci](index.md)
