---
title: '&lt;httpWebRequest&gt; elementu (ustawienia sieciowe)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 1d1dce38e5188824ba1412d3f2a285bd2304f147
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt; elementu (ustawienia sieciowe)
Dostosowuje parametry żądania sieci Web.  
  
 \<Konfiguracja >  
\<system.net>  
\<Ustawienia >  
\<httpWebRequest >  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<httpWebRequest  
  maximumResponseHeadersLength="size"  
  maximumErrorResponseLength="size"  
  maximumUnauthorizedUploadLength="size"  
  useUnsafeHeaderParsing="true|false"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|**Atrybut**|**Opis**|  
|-------------------|---------------------|  
|`maximumResponseHeadersLength`|Określa maksymalną długość nagłówka odpowiedzi w kilobajtach. Wartość domyślna to 64. Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na nagłówków odpowiedzi.|  
|`maximumErrorResponseLength`|Określa maksymalną długość odpowiedzi błędu, w kilobajtach. Wartość domyślna to 64. Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na odpowiedzi na błąd.|  
|`maximumUnauthorizedUploadLength`|Określa maksymalną długość przekazywania w odpowiedzi na kod błędu nieautoryzowanego, w bajtach. Wartość domyślna to -1. Wartość -1 wskazuje, że nie ma limitu rozmiaru będzie nakładać na przekazywanie.|  
|`useUnsafeHeaderParsing`|Określa, czy włączone jest niebezpieczne nagłówka podczas analizowania. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Służy do konfigurowania opcji sieci podstawowej dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie program .NET Framework ściśle wymusza RFC 2616 podczas analizowania identyfikatora URI. Niektóre odpowiedzi serwera może zawierać znaków kontrolnych w polach zabronione, co spowoduje <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metodę, aby zgłosić <xref:System.Net.WebException>. Jeśli **useUnsafeHeaderParsing** ustawiono **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nie zgłosi wyjątku w takim przypadku; jednak, aplikacja będzie narażony na kilka rodzajów ataków analizy identyfikatora URI. Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawiera znaków kontrolnych.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określ większy niż normalne nagłówka maksymalną długość.  
  
```xml  
<configuration>  
  <system.net>  
    <settings>  
      <httpWebRequest  
        maximumResponseHeadersLength="128"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
