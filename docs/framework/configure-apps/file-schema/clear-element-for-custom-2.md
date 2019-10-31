---
title: element <clear> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3e27bb7e21baf2eb4990d0107db4aae1b5f9a7d1
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119071"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Wyczyść element > dla NameValueSectionHandler i DictionarySectionHandler

Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

## <a name="syntax"></a>Składnia

```xml
<clear />
```

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ------------|
| [ **\<sectionname >** Postaci](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Można użyć elementu **\<clear >** , aby usunąć wszystkie ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

Ten przykład definiuje plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazuje, jak używać **\<wyczyść >** elementu w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w pliku konfiguracyjnym komputera.

Następujący kod pliku konfiguracji komputera deklaruje sekcję **\<sekcji >** :

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
  </configSections>
  <mySection>
    <add key="key1" value="value1" />
    <add key="key2" value="value2" />
  </mySection>
</configuration>
```

Następujący kod pliku konfiguracyjnego aplikacji usuwa wszystkie ustawienia z **\<sekcji >** . Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w sekcji **\<** sekcji w pliku konfiguracji maszyny.

```xml
<!-- Application configuration file -->
<configuration>
  <mySection>
    <clear/>
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
