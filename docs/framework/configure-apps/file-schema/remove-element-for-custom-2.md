---
title: element <remove> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: mairaw
ms.author: mairaw
ms.openlocfilehash: dc1519a794e24e04074dd2a674ecc2c0f3666521
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73118567"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<usunąć elementu > dla NameValueSectionHandler i DictionarySectionHandler

Usuwa poprzednio zdefiniowane ustawienie.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**

## <a name="syntax"></a>Składnia

```xml
<add remove="key" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **głównych**   | Atrybut wymagany.<br><br>Określa nazwę ustawienia do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

| Element | Opis |
| ------- | ------------|
| [ **\<sectionname >** Postaci](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Można użyć elementu **\<remove >** , aby usunąć ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak za pomocą **\<usunąć >** elementu w pliku konfiguracyjnym aplikacji usunąć ustawienia zdefiniowane wcześniej w pliku konfiguracyjnym komputera.

Poniższy kod pliku konfiguracji komputera deklaruje sekcję **\<sekcji >** i dodaje do niej dwa ustawienia, `key1` i `key2`:

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

Następujący kod pliku konfiguracji aplikacji usuwa ustawienie `key2` z **\<sekcji >** :

```xml
<!--Application configuration file -->
<configuration>
  <mySection>
    <remove key="key2" />
  </mySection>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
