---
title: element <clear> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
ms.openlocfilehash: f6d860f35d22002030ffa3d09dd0d8a96116bf5e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214745"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Wyczyść element > dla NameValueSectionHandler i DictionarySectionHandler

Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.

[ **\<> konfiguracji**](configuration-element.md)\
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

## <a name="syntax"></a>Składnia

```xml
<clear />
```

## <a name="attributes"></a>Atrybuty

None

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ------------|
| [ **\<sectionname >** Postaci](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementy podrzędne

None

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

Następujący kod pliku konfiguracyjnego aplikacji usuwa wszystkie ustawienia z **\<sekcji >** . Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w sekcji **>\<** sekcji w pliku konfiguracji maszyny.

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

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
