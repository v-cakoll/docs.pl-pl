---
title: element <add> dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a9e7d68530ae1f0666fc4940ffe7605c3bf8dfe3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119614"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<dodać elementu > dla NameValueSectionHandler i DictionarySectionHandler

Dodaje niestandardowe ustawienia aplikacji. Każdy **\<Dodaj tag >** zawiera parę klucz/wartość.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sectionname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**

## <a name="syntax"></a>Składnia

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
| --------- | ----------- |
| **głównych**   | Atrybut wymagany.<br><br>Określa nazwę ustawienia. |
| **value** | Atrybut wymagany.<br><br>Określa wartość ustawienia. |

## <a name="parent-element"></a>Element nadrzędny

| Element | Opis |
| ------- | ------------|
| [ **\<sectionname >** Postaci](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej i użyć **\<dodaj >** elementu, aby umieścić ustawienia w sekcji:

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
