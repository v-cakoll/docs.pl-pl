---
title: Niestandardowy element NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a9722493ec62952d7cbc07d478687b8495d24f95
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Niestandardowy element NameValueSectionHandler i DictionarySectionHandler

Definiuje ustawienia w sekcji Konfiguracja niestandardowa, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<sectionName >**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<Dodaj >** ](~/docs/framework/configure-apps/file-schema/add-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler>  | Dodaje ustawienia aplikacji niestandardowych. |
| [**\<Usuń >** ](~/docs/framework/configure-apps/file-schema/remove-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler> |    Usuwa wcześniej zdefiniowanego ustawienie. |
| [**\<Wyczyść >** ](~/docs/framework/configure-apps/file-schema/clear-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i<xref:System.Configuration.DictionarySectionHandler> | Czyści wszystkie ustawienia zdefiniowane w sekcji. |

## <a name="remarks"></a>Uwagi

**\<SectionName >** element jest elementem niestandardowe zdefiniowane przez  **\<sekcji >** tagów w  **\<configSections >**elementu.

W poniższej tabeli przedstawiono zwraca typ obiektu metody ConfigurationSettings.GetConfig dla każdego modułu obsługi sekcji konfiguracji:

| Program obsługi sekcji konfiguracji                        | Zwracany typ                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób zadeklarować sekcje, które używają <xref:System.Configuration.DictionarySectionHandler> i <xref:System.Configuration.NameValueSectionHandler> klasy. 

Pierwszy element niestandardowy jest  **\<dictionarySample >**, który zawiera ustawienia odczytywane przez <xref:System.Configuration.DictionarySectionHandler> klasy w `System.dll` zestawu. Drugi element niestandardowy jest  **\<mySection >**, który zawiera ustawienia odczytywane przez <xref:System.Configuration.NameValueSectionHandler> klasy w `System.dll` zestawu.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
