---
title: <clear> — element do <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: guardrex
ms.author: mairaw
ms.openlocfilehash: d824ae828dd025f3292990facaa5e423add9c282
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55254778"
---
# <a name="clear-element-for-configsections"></a>\<Wyczyść >, element dla \<configSections >

Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

## <a name="syntax"></a>Składnia

```xml
<clear/>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Nazwa**  | Atrybut wymagany.<br><br>Określa nazwę sekcji lub grupy sekcji do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<configSections>** Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

 **\<Wyczyść >** elementu usuwa wszystkie sekcje i grup sekcji z Twojej aplikacji, które zostały wcześniej zdefiniowane w bieżącym pliku konfiguracji lub wyższego poziomu w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W tym przykładzie definiuje plik konfiguracji i pliku konfiguracji aplikacji i przedstawia sposób użycia  **\<Wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić wcześniej zdefiniowane w sekcji plik konfiguracji komputera.

Poniższy kod pliku konfiguracji maszyny deklaruje dwie sekcje  **\<sampleSection >** i  **\<anotherSampleSection >**, które są odczytywane przed zastosowaniem plik konfiguracji:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
    <section name="anotherSampleSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowanej sekcje. Aplikacja nie może używać lub pobrać ustawień albo sekcje, które zostały zadeklarowane w pliku konfiguracji komputera. Jednak można użyć ustawień z  **\<anotherSection >** ponieważ pochodzi on po  **\<Wyczyść >** elementu.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <clear/>
    <section name="anotherSection"
             type="System.Configuration.NameValueSectionHandler" />
  </configSections>
  <anotherSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
