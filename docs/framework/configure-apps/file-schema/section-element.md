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
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 64556054df2689ff758f52c7e98556997a3e9d3d
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301173"
---
# <a name="section-element"></a>\<sekcja > element

Zawiera deklarację sekcji konfiguracji.

[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<sekcja >**

[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sectionGroup>** ](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)   
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<sekcja >**

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
| **name**  | Określa nazwę sekcji konfiguracji. |
| **type**  | Określa nazwę klasy programu obsługi sekcji konfiguracji, które odczytuje sekcji w pliku konfiguracji. Wartość typu ma składnię "fully-qualified-section-handler-class-name simple zestawu name". Nazwa zestawu prostych jest nazwą pliku głównego bez *.dll* rozszerzenie pliku. |

## <a name="optional-attributes"></a>Opcjonalne atrybuty

Następujące atrybuty mają zastosowanie tylko w przypadku aplikacji ASP.NET. System konfiguracji ignoruje te atrybuty dla innych typów aplikacji.

|                     | Opis |
| ------------------- | ----------- |
| **allowDefinition** | Określa plik konfiguracji, który można używać w sekcji. Użyj jednej z następujących wartości:<br><br>**Wszędzie**<br>Umożliwia sekcji, aby można używać w dowolnym pliku konfiguracji. Domyślnie włączone.<br>**MachineOnly**<br>Zezwala na sekcji, który ma być używany tylko w pliku konfiguracji komputera (*Machine.config*).<br>**MachineToApplication**<br>Umożliwia sekcji do użycia w pliku konfiguracji komputera lub pliku konfiguracji aplikacji. |
| **allowLocation**   | Określa, czy sekcja może być używany w ramach  **\<lokalizacja >** elementu. Użyj jednej z następujących wartości:<br><br>**true**<br>Zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu. Domyślnie włączone.<br>**false**<br>Nie zezwala na sekcji, aby można używać wewnątrz  **\<lokalizacja >** elementu. |

## <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [ **\<configSections>** Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji. |
| [ **\<sectionGroup>** Element](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracji. |

> [!NOTE]
> A  **\<sekcji >** element jest elementem podrzędnym jednej  **\<configSections >** lub  **\<sectionGroup >** , ale nie oba.

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Deklarowanie sekcji konfiguracji zasadniczo definiuje nowy element pliku konfiguracji. Nowy element zawiera ustawienia, że konfiguracja sekcji obsługi (to znaczy, klasę, która implementuje <xref:System.Configuration.IConfigurationSectionHandler> interfejsu) odczytuje. Atrybuty i elementy podrzędne sekcji, jaką zdefiniujesz zależą od obsługi sekcji, używane do odczytywania ustawień.

Deklarowanie program obsługi sekcji konfiguracji w *Machine.config* pliku umożliwia używanie sekcji konfiguracji w pliku konfiguracyjnym dowolnej aplikacji na tym komputerze, chyba że **allowDefinition**atrybutu określi inaczej.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje jak zdefiniować sekcję konfiguracji i zdefiniować ustawienia dla tej sekcji:

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

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
