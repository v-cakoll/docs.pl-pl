---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
ms.openlocfilehash: 55116f1fe6fdffffea8f26d8a4de783c7305ada3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155352"
---
# <a name="configsections-element-for-configuration"></a>\<configSeks> element do \<> konfiguracyjnego

Zawiera sekcje konfiguracji i deklaracje obszaru nazw.

konfiguracja &nbsp; &nbsp;>[** \<**](configuration-element.md) ** \<konfiguracjeSekcje>**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<>konfiguracyjne**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<>sekcji**](section-element.md) | Zawiera deklarację sekcji konfiguracji. |
| [**\<sectionGrupa>**](sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracji. |
| [**\<usuń>**](remove-element-for-configsections.md) | Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji. |
| [**\<wyraźne>**](clear-element-for-configsections.md) | Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji. |

## <a name="remarks"></a>Uwagi

Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem podrzędnym ** \<elementu konfiguracji>.**

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:

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
