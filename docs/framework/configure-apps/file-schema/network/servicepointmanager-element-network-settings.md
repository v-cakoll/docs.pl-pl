---
title: <servicePointManager>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: a6a40d97bf16a3125452311e7762617e657ca384
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659146"
---
# <a name="servicepointmanager-element-network-settings"></a>\<ServicePointManager — element > (Ustawienia sieci)
Konfiguruje połączenia z zasobami sieciowymi.  
  
 \<> konfiguracji  
\<system.net>  
\<settings>  
\<servicePointManager>  
  
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
|`encryptionPolicy`|Określa zasady szyfrowania stosowane do sesji SSL/TLS w <xref:System.Net.ServicePointManager> wystąpieniu. Możliwe wartości są równoważne z wartościami <xref:System.Net.Security.EncryptionPolicy> wyliczenia. Użycie <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagane, gdy zasady szyfrowania są ustawione na `NoEncryption`. Wartość domyślna to `RequireEncryption`.|  
|`expect100Continue`|Określa, `100-continue` czy metody post powinny oczekiwać odpowiedzi z serwera. Wartość domyślna to `true`.|  
|`useNagleAlgorithm`|Określa, czy połączenia kontrolowane przez Menedżera punktów usług używają algorytmu nagle. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schemat ustawień sieci](index.md)
