---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 8fae3673fe72d036802cb1a8366aaa2430c38884
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927500"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Element niestandardowy dla SingleTagSectionHandler

Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<sekcję > elementu i <xref:System.Configuration.SingleTagSectionHandler> używa klasy.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp; *\<sectionName>*

## <a name="syntax"></a>Składnia

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atrybuty

Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<> konfiguracji**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Element **SectionName > jest elementem niestandardowym zdefiniowanym przez tag > sekcji w elemencie > configSections. \<** [ **\<** ](section-element.md) [ **\<** ](configsections-element-for-configuration.md) System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje element niestandardowy o nazwie  **\<sampleSection >** , który zawiera <xref:System.Configuration.SingleTagSectionHandler> ustawienia odczytane przez klasę:

```xml
<configuration>
  <configSections>
    <section name="sampleSection" 
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
