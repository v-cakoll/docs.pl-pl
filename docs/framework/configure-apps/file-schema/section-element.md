---
title: '&lt;sekcja&gt; — element'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/section
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup/section
helpviewer_keywords:
- section Element
- <section> Element
ms.assetid: ec7d4110-2403-47ac-8218-499bfe9d5ddb
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 17b44ca93efc26f4732f5fe2926f894257d8f984
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32746439"
---
# <a name="section-element"></a>\<sekcja > — element

Zawiera deklaracji sekcji konfiguracji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<sekcja >**

## <a name="syntax"></a>Składnia

```xml
<section name="section name"
         type="configuration section handler class, assembly"
         allowDefinition="Everywhere|MachineOnly|MachineToApplication" 
         allowLocation="true|false" />
```

## <a name="required-attributes"></a>Wymaganych atrybutów

|           | Opis |
| --------- | ----------- |
| **Nazwa**  | Określa nazwę sekcji konfiguracji. |
| **Typ**  | Określa nazwę klasy obsługi sekcji konfiguracji, która odczytuje sekcji w pliku konfiguracji. Wartość typu ma składnię "fully-qualified-section-handler-class-name, prosty zestawu name". Nazwa zestawu prostych jest nazwa głównego pliku bez *.dll* rozszerzenia pliku. |

## <a name="optional-attributes"></a>Opcjonalne atrybuty

Następujące atrybuty są stosowane tylko do aplikacji ASP.NET. System konfiguracji ignoruje te atrybuty dla różnych typów aplikacji.

|                     | Opis |
| ------------------- | ----------- |
| **allowDefinition** | Określa do jakiego sekcji mogą być używane w pliku konfiguracji. Użyj jednej z następujących wartości:<br><br>**Wszędzie**<br>Umożliwia sekcji, aby można używać w dowolnym pliku konfiguracji. Domyślnie włączone.<br>**MachineOnly**<br>Umożliwia sekcji, aby można używać tylko w pliku konfiguracji komputera (*Machine.config*).<br>**MachineToApplication**<br>Umożliwia sekcji do użycia w pliku konfiguracyjnym maszyny lub pliku konfiguracji aplikacji. |
| **allowLocation**   | Określa, czy sekcja mogą być używane w ramach  **\<lokalizacji >** elementu. Użyj jednej z następujących wartości:<br><br>**true**<br>Umożliwia sekcji do użycia w  **\<lokalizacji >** elementu. Domyślnie włączone.<br>**false**<br>Nie zezwalaj na sekcji do użycia w  **\<lokalizacji >** elementu. |

## <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<configSections >** — Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Zawiera konfigurację deklaracji sekcji i przestrzeni nazw. |
| [**\<sectionGroup >** — Element](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracyjnych. |

> [!NOTE]
> A  **\<sekcji >** element jest elementem podrzędnym albo  **\<configSections >** lub  **\<sectionGroup >** , ale nie oba.

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Deklarowanie sekcji konfiguracji zasadniczo definiuje nowego elementu w pliku konfiguracji. Nowy element zawiera ustawienia, że konfiguracja sekcji obsługi (to znaczy, że klasa implementująca <xref:System.Configuration.IConfigurationSectionHandler> interfejsu) odczytuje. Atrybuty i elementy podrzędne sekcji definiowane są zależne od modułu obsługi sekcji, używaną do odczytu ustawień.

Deklarowanie modułu obsługi sekcji konfiguracji w *Machine.config* pliku pozwala na użycie sekcji konfiguracji w żadnym pliku konfiguracji aplikacji na tym komputerze, chyba że **allowDefinition**atrybut określa, w przeciwnym razie wartość.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak planować sekcji konfiguracji i określać ustawienia dla tej sekcji:

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

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
