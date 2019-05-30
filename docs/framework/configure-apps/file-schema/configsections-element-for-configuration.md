---
title: <configSections>, element dla <configuration>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: d522d004630dee942e24c39a936feae7dc957bd5
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66300790"
---
# <a name="configsections-element-for-configuration"></a>\<configSections >, element dla \<konfiguracji >

Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.

[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp; **\<configSections>**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [ **\<sekcja >** ](~/docs/framework/configure-apps/file-schema/section-element.md) | Zawiera deklarację sekcji konfiguracji. |
| [ **\<sectionGroup>** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracji. |
| [ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji. |
| [ **\<clear>** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji. |

## <a name="remarks"></a>Uwagi

Jeśli ten element znajduje się w pliku konfiguracji, musi to być pierwszy element podrzędny elementu  **\<konfiguracji >** elementu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:

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

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
