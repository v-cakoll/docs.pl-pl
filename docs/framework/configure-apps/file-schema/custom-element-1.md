---
title: Niestandardowy element SingleTagSectionHandler
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords: custom element
ms.assetid: e62056c6-b351-40eb-afc0-cc13fc44e45e
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 496967bc3638344d2b39d428b85270b575b325ed
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="custom-element-for-singletagsectionhandler"></a>Niestandardowy element SingleTagSectionHandler

Definiuje ustawienia w sekcji Konfiguracja niestandardowa, która jest definiowana za pomocą <section> element i używa <xref:System.Configuration.SingleTagSectionHandler> klasy.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;*\<sectionName >*

## <a name="syntax"></a>Składnia

```xml
<sectionName key="value" key2="value2" ... />
```

## <a name="attributes"></a>Atrybuty

Atrybuty i wartości atrybutów są zdefiniowane przez użytkownika.

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<SectionName >** element jest elementem niestandardowe zdefiniowane przez [  **\<sekcji >** ](~/docs/framework/configure-apps/file-schema/section-element.md) tagów w [  **\<configSections >** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) elementu. System konfiguracji zwraca <xref:System.Collections.IDictionary> obiektu po wywołaniu <xref:System.Configuration.Configuration.GetSection(System.String)?displayProperty=nameWithType>.

## <a name="example"></a>Przykład

Poniższy przykład deklaruje elementu niestandardowego o nazwie  **\<sampleSection >** zawierający ustawienia odczytywane przez <xref:System.Configuration.SingleTagSectionHandler> klasy:

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

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
