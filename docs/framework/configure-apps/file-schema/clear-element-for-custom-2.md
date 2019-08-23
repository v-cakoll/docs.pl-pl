---
title: <clear>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: ff2294ec-fb82-4b0c-933e-ae185433fc7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: fbb689db4abc5d59729d9a4d9807a02a0983d40b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927713"
---
# <a name="clear-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Wyczyść element > dla NameValueSectionHandler i DictionarySectionHandler

Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

## <a name="syntax"></a>Składnia

```xml
<clear />
```

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ------------|
| [sekcjaname > element  **\<** ](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler> |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Można użyć elementu  **\<Clear >** , aby usunąć wszystkie ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W tym przykładzie zdefiniowano plik konfiguracji komputera i plik konfiguracji aplikacji oraz pokazano,  **\<** jak używać elementu Clear > w pliku konfiguracyjnym aplikacji, aby wyczyścić sekcje wcześniej zdefiniowane w konfiguracji maszyny rozszerzeniem.

Następujący kod pliku konfiguracji komputera deklaruje sekcję  **\<>** :

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

Następujący kod pliku konfiguracji aplikacji usuwa wszystkie ustawienia z  **\<sekcji >** . Aplikacja nie może pobrać z ustawień, które zostały zadeklarowane w sekcji  **\<>** w pliku konfiguracji maszyny.

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
