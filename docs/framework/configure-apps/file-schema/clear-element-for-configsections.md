---
title: <clear>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a45572d0dcb2737558e11f5c38ac2ccc338c754a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119085"
---
# <a name="clear-element-for-configsections"></a>\<Wyczyść > elementu \<configSections >

Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

## <a name="syntax"></a>Składnia

```xml
<clear/>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Nazwij**  | Atrybut wymagany.<br><br>Określa nazwę sekcji lub grupy sekcji do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<configSections >** Postaci](configsections-element-for-configuration.md) | Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<clear >** usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w pliku konfiguracyjnym komputera.

Następujący kod pliku konfiguracji komputera deklaruje dwie sekcje, **\<sampleSection >** i **\<anotherSampleSection >** , które są odczytywane przed plikiem konfiguracyjnym aplikacji:

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

Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje. Aplikacja nie może używać lub pobrać ustawień w żadnej z sekcji zadeklarowanych w pliku konfiguracji maszyny. Może jednak używać ustawień z **\<anotherSection >** , ponieważ jest on dostępny po **\<Wyczyść >** elementu.

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

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
