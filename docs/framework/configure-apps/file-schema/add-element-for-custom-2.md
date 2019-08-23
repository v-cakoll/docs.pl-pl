---
title: <add>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 0d4ddb53-eb2b-49c0-9c33-a8dec5c39b46
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: ec6d5045580e887de5f05a05c8f39fa62c6e3f2e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921331"
---
# <a name="add-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Dodaj element > dla NameValueSectionHandler i DictionarySectionHandler

Dodaje niestandardowe ustawienia aplikacji. Każdy tag Add > zawiera parę klucz/wartość.  **\<**

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<add>**

## <a name="syntax"></a>Składnia

```xml
<add key="key" value="value" />
```

## <a name="attributes"></a>Atrybuty

| Atrybut | Opis |
| --------- | ----------- |
| **Klucz**   | Atrybut wymagany.<br><br>Określa nazwę ustawienia. |
| **value** | Atrybut wymagany.<br><br>Określa wartość ustawienia. |

## <a name="parent-element"></a>Element nadrzędny

| Element | Opis |
| ------- | ------------|
| [sekcjaname > element  **\<** ](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler> |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zdefiniować sekcję konfiguracji niestandardowej i użyć  **\<elementu Dodaj >** , aby umieścić ustawienia w sekcji:

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
