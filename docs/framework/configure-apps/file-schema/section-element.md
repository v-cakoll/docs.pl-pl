---
title: <section> — element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a7147173dc9f132fa2dd14d20526d59927a183bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73115264"
---
# <a name="section-element"></a>\<sekcja >

Zawiera deklarację sekcji konfiguracyjnej.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<**

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sekcja**](sectiongroup-element-for-configsections.md) >   
&nbsp;&nbsp;&nbsp;&nbsp; **&nbsp;&nbsp;\<** >

## <a name="syntax"></a>Składnia

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Wymagane atrybuty

|           | Opis |
| --------- | ----------- |
| **Nazwij**  | Określa nazwę sekcji konfiguracji. |
| **Wprowadź**  | Określa nazwę klasy procedury obsługi sekcji konfiguracji, która odczytuje sekcję z pliku konfiguracyjnego. Wartość typu ma składnię "w pełni kwalifikowana-sekcja-Handler-class-name, Simple-Assembly-Name". Prosta nazwa zestawu to główna nazwa pliku bez rozszerzenia pliku *dll* . |

## <a name="optional-attributes"></a>Atrybuty opcjonalne

Następujące atrybuty są stosowane tylko w przypadku aplikacji ASP.NET. System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.

|                     | Opis |
| ------------------- | ----------- |
| **allowDefinition** | Określa plik konfiguracji, w którym można użyć sekcji. Użyj jednej z następujących wartości:<br><br>**Tam**<br>Zezwala na używanie sekcji w dowolnym pliku konfiguracyjnym. Domyślnie włączone.<br>**MachineOnly**<br>Zezwala na użycie sekcji tylko w pliku konfiguracji komputera (*Machine. config*).<br>**MachineToApplication**<br>Zezwala na używanie sekcji w pliku konfiguracji komputera lub pliku konfiguracyjnym aplikacji. |
| **allowLocation**   | Określa, czy sekcja może być używana w **\<lokalizacji >** elementu. Użyj jednej z następujących wartości:<br><br>**true**<br>Zezwala na używanie sekcji w **\<lokalizacji >** elementu. Domyślnie włączone.<br>**false**<br>Nie zezwala na używanie sekcji w **\<lokalizacji >** elementu. |

## <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [ **\<configSections >** Postaci](configsections-element-for-configuration.md) | Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw. |
| [ **\<sekcji >** Postaci](sectiongroup-element-for-configsections.md) | Definiuje przestrzeń nazw dla sekcji konfiguracyjnych. |

> [!NOTE]
> **\<sekcja >** jest elementem podrzędnym **\<configSections >** lub **\<** , ale nie obu.

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji. Nowy element zawiera ustawienia, które są używane przez sekcję konfiguracyjną (czyli klasy implementującej interfejs <xref:System.Configuration.IConfigurationSectionHandler>). Atrybuty i elementy podrzędne zdefiniowanej sekcji zależą od procedury obsługi sekcji używanej do odczytywania ustawień.

Deklarowanie procedury obsługi sekcji konfiguracji w pliku *Machine. config* umożliwia korzystanie z sekcji konfiguracji w dowolnym pliku konfiguracyjnym aplikacji na tym komputerze, chyba że atrybut **AllowDefinition** określa inaczej.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracyjną i zdefiniować ustawienia dla tej sekcji:

```xml
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" 
             allowLocation="false" />
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
