---
title: <clear>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
ms.openlocfilehash: 66abd7f057bc6d060e50a889a945281d07c97592
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "79155430"
---
# <a name="clear-element-for-configsections"></a>\<clear>, element dla \<configSections>

Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.

[**\<configuration>**](configuration-element.md) &nbsp;&nbsp;[**\<configSections>**](configsections-element-for-configuration.md) &nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**

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
| [**\<configSections>** Postaci](configsections-element-for-configuration.md) | Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<clear>** Element usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<clear>** elementu w pliku konfiguracyjnym aplikacji do czyszczenia sekcji wcześniej zdefiniowanych w pliku konfiguracyjnym komputera.

Następujący kod pliku konfiguracji komputera deklaruje dwie sekcje **\<sampleSection>** i **\<anotherSampleSection>** , które są odczytywane przed plikiem konfiguracyjnym aplikacji:

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

Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje. Aplikacja nie może używać lub pobrać ustawień w żadnej z sekcji zadeklarowanych w pliku konfiguracji maszyny. Może jednak używać ustawień z **\<anotherSection>** , ponieważ znajduje się po **\<clear>** elemencie.

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
