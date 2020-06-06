---
title: Element niestandardowy dla SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: a40f35838655f6021af0b2e966335803ec8c16b4
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "80635399"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Element niestandardowy dla SingleTagSectionHandler

Definiuje ustawienia w sekcji konfiguracji niestandardowej zdefiniowanej przez \<section> element i używa <xref:System.Configuration.SingleTagSectionHandler> klasy.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;*\<sectionName>*

## <a name="syntax"></a>Składnia

```xml
<sectionName key="value" key2="value2" />
```

## <a name="attributes"></a>Atrybuty

Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<configuration>**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<sectionName>** Element jest elementem niestandardowym zdefiniowanym przez [**\<section>**](section-element.md) tag w [**\<configSections>**](configsections-element-for-configuration.md) elemencie. System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas wywoływania <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType> .

## <a name="example"></a>Przykład

Poniższy przykład deklaruje element niestandardowy o nazwie **\<sampleSection>** , który zawiera ustawienia odczytane przez <xref:System.Configuration.SingleTagSectionHandler> klasę:

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
