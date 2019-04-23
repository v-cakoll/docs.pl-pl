---
title: <httpWebRequest>, element (ustawienia sieci)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/httpWebRequest
- http://schemas.microsoft.com/.NetConfiguration/v2.0#httpWebRequest
helpviewer_keywords:
- <httpWebRequest> element
- httpWebRequest element
ms.assetid: 52acd9d2-5bdc-4dc4-9c2a-f0a476ccbb31
ms.openlocfilehash: 722b2f726c9085f6dee6bad82044da3011b98702
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59169302"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest >, Element (ustawienia sieci)
Dostosowuje parametry żądania sieci Web.  
  
 \<Konfiguracja >  
\<system.net>  
\<settings>  
\<httpWebRequest>  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Net.HttpWebRequest.MaximumResponseHeadersLength%2A>
- [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
