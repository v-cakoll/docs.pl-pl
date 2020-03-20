---
title: Element niestandardowy dla usługi SingleTagSectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
ms.openlocfilehash: 04360a796b18cf1e414f1f84bff247a1e9d8ef9c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155157"
---
# <a name="custom-element-for-singletagsectionhandler"></a>Element niestandardowy dla usługi SingleTagSectionHandler

Definiuje ustawienia w sekcji konfiguracji niestandardowej, \<która jest zdefiniowana przez <xref:System.Configuration.SingleTagSectionHandler> element> sekcji i używa klasy.

&nbsp; [**>\<konfiguracji**](configuration-element.md) &nbsp; * \<*

## <a name="syntax"></a>Składnia

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atrybuty

Atrybuty i wartości atrybutów są definiowane przez użytkownika.

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<>konfiguracyjne**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Element ** \<>sectionName** jest elementem niestandardowym [** \<**](section-element.md) zdefiniowanym przez znacznik>sekcji w [** \<konfistycznym>elemencie.**](configsections-element-for-configuration.md) System konfiguracji zwraca <xref:System.Collections.IDictionary> obiekt podczas <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>wywoływania .

## <a name="example"></a>Przykład

Poniższy przykład deklaruje element niestandardowy o nazwie <xref:System.Configuration.SingleTagSectionHandler> ** \<sampleSekcja>,** która zawiera ustawienia odczytane przez klasę:

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

Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](index.md)
