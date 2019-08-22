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
ms.openlocfilehash: de5672e5c6762b1e0742e717a3d499a4f93ee8ec
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69659341"
---
# <a name="httpwebrequest-element-network-settings"></a>\<httpWebRequest >, element (Ustawienia sieci)
Dostosowuje parametry żądania sieci Web.  
  
 \<> konfiguracji  
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
|`maximumResponseHeadersLength`|Określa maksymalną długość nagłówka odpowiedzi w kilobajtach. Wartość domyślna to 64. Wartość-1 oznacza, że w nagłówkach odpowiedzi nie zostanie wprowadzony limit rozmiaru.|  
|`maximumErrorResponseLength`|Określa maksymalną długość odpowiedzi na błąd w kilobajtach. Wartość domyślna to 64. Wartość-1 oznacza, że w odpowiedzi na błąd nie zostanie wprowadzony limit rozmiaru.|  
|`maximumUnauthorizedUploadLength`|Określa maksymalną długość przekazywania w odpowiedzi na nieautoryzowany kod błędu w bajtach. Wartość domyślna to-1. Wartość-1 oznacza, że żaden limit rozmiaru nie zostanie nałożony na przekazywanie.|  
|`useUnsafeHeaderParsing`|Określa, czy jest włączone analizowanie niebezpiecznego nagłówka. Wartość domyślna to `false`.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Ustawienia](settings-element-network-settings.md)|Konfiguruje podstawowe opcje sieci dla <xref:System.Net> przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie .NET Framework ściśle wymusza analizowanie identyfikatorów URI w dokumencie RFC 2616. Niektóre odpowiedzi serwera mogą zawierać znaki kontrolne w zabronionych polach, co spowoduje <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> , że metoda <xref:System.Net.WebException>wygeneruje. Jeśli **UseUnsafeHeaderParsing** ma **wartość true**, <xref:System.Net.HttpWebRequest.GetResponse?displayProperty=nameWithType> program nie będzie zgłaszany w tym przypadku, jednak aplikacja będzie narażona na kilka form ataków dotyczących analizy identyfikatorów URI. Najlepszym rozwiązaniem jest zmiana serwera tak, aby odpowiedź nie zawierała znaków kontrolnych.  
  
## <a name="configuration-files"></a>Pliki konfiguracji  
 Tego elementu można użyć w pliku konfiguracyjnym aplikacji lub pliku konfiguracji komputera (Machine. config).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić większą niż normalną maksymalną długość nagłówka.  
  
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
- [Schemat ustawień sieci](index.md)
