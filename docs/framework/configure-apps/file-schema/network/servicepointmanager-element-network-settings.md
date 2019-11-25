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
ms.openlocfilehash: b7333016fea2d46285d3c98181c0ca4904c376f8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/14/2019
ms.locfileid: "74089124"
---
# <a name="servicepointmanager-element-network-settings"></a>\<element > ServicePointManager (Ustawienia sieci)
Konfiguruje połączenia z zasobami sieciowymi.  

[ **\<configuration >** ](../configuration-element.md) \
&nbsp;&nbsp;[ **\<system. net >** ](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](settings-element-network-settings.md) >
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Servicepointmanager >**

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
|`encryptionPolicy`|Określa zasady szyfrowania stosowane do sesji SSL/TLS w wystąpieniu <xref:System.Net.ServicePointManager>. Możliwe wartości są równoważne wartościom wyliczenia <xref:System.Net.Security.EncryptionPolicy>. Użycie <xref:System.Security.Authentication.CipherAlgorithmType.Null> jest wymagane, gdy zasady szyfrowania są ustawione na `NoEncryption`. Wartość domyślna to `RequireEncryption`.|  
|`expect100Continue`|Określa, czy metody POST powinny oczekiwać, że odpowiedź na `100-continue` z serwera ma być odbierana. Wartość domyślna to `true`.|  
|`useNagleAlgorithm`|Określa, czy połączenia kontrolowane przez Menedżera punktów usług używają algorytmu nagle. Wartość domyślna to `true`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla przestrzeni nazw <xref:System.Net>.|  
  
## <a name="remarks"></a>Uwagi  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schemat ustawień sieci](index.md)
