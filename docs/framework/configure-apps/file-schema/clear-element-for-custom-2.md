---
title: '&lt;Wyczyść&gt; element dla NameValueSectionHandler i DictionarySectionHandler'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 55925ee5e9c5a17f14bd199125dbaacbadb9d928
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54720944"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Wyczyść >, element dla NameValueSectionHandler i DictionarySectionHandler

Czyści wszystkie wcześniej zdefiniowane ustawienia w sekcji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<sectionName>**](~/docs/framework/configure-apps/file-schema/custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Składnia

```xml
<clear />
```

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ------------|
| [**\<parametrami sectionName >** — Element](~/docs/framework/configure-apps/file-schema/custom-element-2.md) | Definiuje ustawienia powiązane z sekcji konfiguracji niestandardowej, korzystających z <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> klasy. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Możesz użyć  **\<Wyczyść >** elementu do usunięcia wszystkich ustawień z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W tym przykładzie definiuje plik konfiguracji i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji komputera.

Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<mySection >**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Poniższy kod pliku konfiguracji aplikacji spowoduje usunięcie wszystkich ustawień z  **\<mySection >**. Aplikacja nie może pobrać dowolne z ustawień, które zostały zadeklarowane w w  **\<mySection >** sekcję pliku konfiguracji komputera.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
