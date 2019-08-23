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
ms.openlocfilehash: 31b53837e24029fc7ff0b576d95c0213041a434e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927673"
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elementu \<konfiguracji >

Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp; **\<configSections >**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<> konfiguracji**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [ **\<sekcja >** ](section-element.md) | Zawiera deklarację sekcji konfiguracyjnej. |
| [ **\<sectionGroup>** ](sectiongroup-element-for-configsections.md) | Definiuje przestrzeń nazw dla sekcji konfiguracyjnych. |
| [ **\<remove>** ](remove-element-for-configsections.md) | Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji. |
| [ **\<clear>** ](clear-element-for-configsections.md) | Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji. |

## <a name="remarks"></a>Uwagi

Jeśli ten element znajduje się w pliku konfiguracji, musi być pierwszym elementem  **\<** podrzędnym elementu Configuration >.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:

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
