---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 1d0431085a04d3fb817dfe0883779acc4d693084
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214783"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Element niestandardowy dla SingleTagSectionHandler

Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<sekcję > elementu i używa klasy <xref:System.Configuration.SingleTagSectionHandler>.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp; *\<sectionname >*

## <a name="syntax"></a>Składnia

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atrybuty

Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **> konfiguracji \<** ](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

None

## <a name="remarks"></a>Uwagi

**\<sectionname >** element jest elementem niestandardowym zdefiniowanym przez [ **\<sekcję >** ](section-element.md) tagu w\<elementu > [**configSections**](configsections-element-for-configuration.md) . System konfiguracji zwraca obiekt <xref:System.Collections.IDictionary> podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje element niestandardowy o nazwie **\<sampleSection >** , który zawiera ustawienia odczytane przez klasę <xref:System.Configuration.SingleTagSectionHandler>:

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

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
