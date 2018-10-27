---
title: '&lt;httpWebRequest&gt; — Element (ustawienia sieci)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 586b3e7219c72b6cd00653d6d0be3a74f6359709
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50048986"
---
# <a name="lthttpwebrequestgt-element-network-settings"></a>&lt;httpWebRequest&gt; — Element (ustawienia sieci)
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
|`maximumResponseHeadersLength`|Określa maksymalną długość nagłówka żądania, w kilobajtach. Wartość domyślna to 64. Wartość -1 wskazuje, że nie mają limitu rozmiaru zostaną nałożone na nagłówki odpowiedzi.|  
|`maximumErrorResponseLength`|Określa maksymalną długość odpowiedź na błąd, w kilobajtach. Wartość domyślna to 64. Wartość -1 wskazuje, że nie mają limitu rozmiaru zostaną nałożone na odpowiedzi na błąd.|  
|`maximumUnauthorizedUploadLength`|Określa maksymalną długość przekazywania w odpowiedzi na błąd dotyczący nieautoryzowanego dostępu kodu, w bajtach. Wartość domyślna to -1. Wartość -1 wskazuje, że nie mają limitu rozmiaru zostaną nałożone na przekazywanie.|  
|`useUnsafeHeaderParsing`|Określa, czy włączone jest niebezpieczne nagłówka podczas analizowania. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Konfiguruje opcje sieciowe podstawowe dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie program .NET Framework ściśle wymusza dokumencie RFC 2616 podczas analizowania identyfikatora URI. Niektóre odpowiedzi serwera może zawierać znaków kontrolnych w zabronionej pól, które spowoduje, że <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> metodę, aby zgłosić <xref:System.Net.WebException>. Jeśli **useUnsafeHeaderParsing** ustawiono **true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> nie zgłosi wyjątku w tym przypadku; jednakże, Twoja aplikacja będzie narażony na kilka rodzajów ataków analizy identyfikatora URI. Najlepszym rozwiązaniem jest zmiana serwera, tak aby odpowiedź nie zawiera znaków kontrolnych.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Ten element może być użyty w pliku konfiguracji aplikacji lub w pliku konfiguracji komputera (Machine.config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić większego niż normalny nagłówka maksymalną długość.  
  
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
