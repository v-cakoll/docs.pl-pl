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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155430"
---
# <a name="clear-element-for-configsections"></a>\<klarowny element> \<dla> konfisekcyjnych

Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.

&nbsp; &nbsp; &nbsp; &nbsp; ** \<** [** \<konfiguracja>**](configuration-element.md) &nbsp; &nbsp; [** \<konfiguracjeSekcje>**](configsections-element-for-configuration.md) jasne>

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
| [** \<configSekcje>** Element](configsections-element-for-configuration.md) | Zawiera sekcje konfiguracji i deklaracje obszaru nazw. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Element ** \<>wyczyść** usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W tym przykładzie definiuje plik konfiguracji komputera i plik konfiguracji aplikacji i pokazuje, jak używać ** \<elementu clear>** w pliku konfiguracji aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w pliku konfiguracji komputera.

Następujący kod pliku konfiguracji komputera deklaruje dwie ** \<sekcje: sampleSekcja>** i ** \<innySampleSection>**, które są odczytywane przed plikiem konfiguracji aplikacji:

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

Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje. Aplikacja nie może używać ani pobierać ustawień w żadnej z sekcji, które zostały zadeklarowane w pliku konfiguracji komputera. Jednak można użyć ustawień z ** \<innegoSekcja>,** ponieważ pochodzi po ** \<element>jasne.**

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

Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](index.md)
