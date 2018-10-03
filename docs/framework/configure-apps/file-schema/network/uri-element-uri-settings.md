---
title: '&lt;Identyfikator URI&gt; — Element (ustawienia identyfikatora Uri)'
ms.date: 03/30/2017
ms.assetid: c22bab8b-477c-4ae4-8498-65ad409e0847
author: mcleblanc
ms.author: markl
ms.openlocfilehash: a58c27500c0258415c12a5fd8e552b3ee43f50e8
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/02/2018
ms.locfileid: "48033210"
---
# <a name="lturigt-element-uri-settings"></a>&lt;Identyfikator URI&gt; — Element (ustawienia identyfikatora Uri)
Zawiera ustawienia, które określają, jak .NET Framework obsługuje adresy URL wyrażone za pomocą uniform resource identifier (URI).  
  
## <a name="schema-hierarchy"></a>Hierarchia schematu  
 [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)  
  
 [\<Identyfikator URI >](../../../../../docs/framework/configure-apps/file-schema/network/uri-element-uri-settings.md)  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<uri>  
</uri>  
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
 Brak.  
  
### <a name="child-elements"></a>Elementy podrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[IDN](../../../../../docs/framework/configure-apps/file-schema/network/idn-element-uri-settings.md)|Określa, jeśli analizy Zinternacjonalizowanych nazw domen (IDN) są stosowane do nazw domen.|  
|[iriParsing](../../../../../docs/framework/configure-apps/file-schema/network/iriparsing-element-uri-settings.md)|Określa, jeśli analizy międzynarodowego identyfikatora zasobów (IRI) są stosowane do <xref:System.Uri> , czy powinna być stosowana IRI podczas analizowania reguły.|  
|[schemeSettings](../../../../../docs/framework/configure-apps/file-schema/network/schemesettings-element-uri-settings.md)|Określa, jak <xref:System.Uri> będzie być analizowana pod kątem określonych systemów.|  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|**Element**|**Opis**|  
|-----------------|---------------------|  
|[Konfiguracja](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|Zawiera ustawienia dla wszystkich przestrzeni nazw.|  
  
## <a name="remarks"></a>Uwagi  
 `uri` Element zawiera ustawienia dla elementów członkowskich <xref:System.Uri> klasy używane przez klasy w <xref:System.Net> przestrzeni nazw. Ustawienia skonfigurować obsługę IRI i IDN.  
  
## <a name="example"></a>Przykład  
  
### <a name="description"></a>Opis  
 W poniższym przykładzie pokazano konfigurację posługują się <xref:System.Uri> klasy w celu obsługi analizowania IRI i nazwy IDN. Przykład czyści także wszystkie ustawienia systemu, a następnie dodaje obsługę nie anulowania zapewnianego element ścieżki zakodowane w formacie procent ograniczniki schemat http.  
  
### <a name="code"></a>Kod  
  
```xml  
<configuration>  
  <uri>  
    <idn enabled="All" />  
    <iriParsing enabled="true" />  
    <schemeSettings>  
      <clear/>  
      <add name="http" genericUriParserOptions="DontUnescapePathDotsAndSlashes"/>  
    </schemeSettings>  
  </uri>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Schemat ustawień sieci](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
