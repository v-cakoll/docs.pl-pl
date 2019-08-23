---
title: <clear>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 77f1d761-ff45-4001-8f36-3a3e5c41fa63
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: c06fca8b83638fb47bedb21863cb9b200cd211f3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927729"
---
# <a name="clear-element-for-configsections"></a>\<Wyczyść element > dla \<configSections >

Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Składnia

```xml
<clear/>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **name**  | Atrybut wymagany.<br><br>Określa nazwę sekcji lub grupy sekcji do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [configSections, element >  **\<** ](configsections-element-for-configuration.md) | Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Element **Clear > usuwa wszystkie sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane wcześniej w bieżącym pliku konfiguracyjnym lub na wyższym poziomie w hierarchii plików konfiguracji. \<**

## <a name="example"></a>Przykład

W tym przykładzie zdefiniowano plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazano,  **\<** jak używać elementu Clear > w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w konfiguracji maszyny rozszerzeniem.

Następujący kod pliku konfiguracji komputera deklaruje dwie sekcje,  **\<sampleSection >** i  **\<anotherSampleSection >** , które są odczytywane przed plikiem konfiguracji aplikacji:

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

Poniższy kod pliku konfiguracji aplikacji czyści wszystkie wcześniej zadeklarowane sekcje. Aplikacja nie może używać lub pobrać ustawień w żadnej z sekcji zadeklarowanych w pliku konfiguracji maszyny. Może jednak używać ustawień z  **\<anotherSection >**  **\<** , ponieważ znajduje się po elemencie Clear >.

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
