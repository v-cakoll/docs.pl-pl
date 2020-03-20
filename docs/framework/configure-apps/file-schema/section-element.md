---
title: <section>  — element
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
ms.openlocfilehash: 88f74c02ef627e9136e4437ffa150c36445266a3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153736"
---
# <a name="section-element"></a>\<element> sekcji

Zawiera deklarację sekcji konfiguracji.

[**\<>konfiguracyjne**](configuration-element.md)\
&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<>sekcji**

[**\<>konfiguracyjne**](configuration-element.md)\
&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGrupa>**](sectiongroup-element-for-configsections.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>sekcji**

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
| **Nazwa**  | Określa nazwę sekcji konfiguracji. |
| **Typu**  | Określa nazwę klasy obsługi sekcji konfiguracji, która odczytuje sekcję z pliku konfiguracji. Wartość typu ma składnię "w pełni kwalifikowana sekcja-handler-class-name, simple-assembly-name". Prosta nazwa zestawu to główna nazwa pliku bez rozszerzenia pliku *.dll.* |

## <a name="optional-attributes"></a>Atrybuty opcjonalne

Następujące atrybuty mają zastosowanie tylko do aplikacji ASP.NET. System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.

|                     | Opis |
| ------------------- | ----------- |
| **zezwalaj NaDefiniowanie** | Określa, w którym pliku konfiguracyjnym może być używany sekcja. Użyj jednej z następujących wartości:<br><br>**Wszędzie**<br>Umożliwia użycie sekcji w dowolnym pliku konfiguracyjnym. Domyślnie włączone.<br>**MaszynaOnująca**<br>Umożliwia użycie sekcji tylko w pliku konfiguracyjnym komputera (*Machine.config*).<br>**Machinetoapplication**<br>Umożliwia użycie sekcji w pliku konfiguracyjnym komputera lub w pliku konfiguracyjnym aplikacji. |
| **allowLocation (zezwalajlokalizacja)**   | Określa, czy sekcja może być używana w ** \<>** element lokalizacji. Użyj jednej z następujących wartości:<br><br>**true**<br>Umożliwia użycie sekcji w obrębie ** \<elementu>lokalizacji.** Domyślnie włączone.<br>**false**<br>Nie zezwala na użycie sekcji w obrębie ** \<>** elementu lokalizacji. |

## <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [** \<configSekcje>** Element](configsections-element-for-configuration.md) | Zawiera sekcje konfiguracji i deklaracje obszaru nazw. |
| [** \<sectionGrupa>** Element](sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracji. |

> [!NOTE]
> Element ** \<>sekcji** jest elementem podrzędnym ** \<konfisycji>** lub ** \<sectionGroup>** ale nie obu.

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element dla pliku konfiguracji. Nowy element zawiera ustawienia, które odczytuje program obsługi sekcji <xref:System.Configuration.IConfigurationSectionHandler> konfiguracji (czyli klasa implementujący interfejs). Atrybuty i elementy podrzędne zdefiniowanej sekcji zależą od programu obsługi sekcji używanego do odczytywania ustawień.

Deklarowanie obsługi sekcji konfiguracji w pliku *Machine.config* umożliwia użycie sekcji konfiguracji w dowolnym pliku konfiguracji aplikacji na tym komputerze, chyba że atrybut **allowDefinition** określa inaczej.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:

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

Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](index.md)
