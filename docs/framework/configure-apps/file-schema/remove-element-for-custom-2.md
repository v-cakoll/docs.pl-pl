---
title: <remove>element dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 8d8af7f5-26c9-4db9-bbe4-b2a4e6949568
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: cd338ff2d613be31ab1524f6baed6107f803a688
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920947"
---
# <a name="remove-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>\<Usuń element > dla NameValueSectionHandler i DictionarySectionHandler

Usuwa poprzednio zdefiniowane ustawienie.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<sekcjaname >** ](custom-element-2.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<remove>**

## <a name="syntax"></a>Składnia

```xml
<add remove="key" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Klucz**   | Atrybut wymagany.<br><br>Określa nazwę ustawienia do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

| Element | Opis |
| ------- | ------------|
| [sekcjaname > element  **\<** ](custom-element-2.md) | Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler> |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Aby usunąć ustawienia z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji, można użyć  **\<elementu Usuń >** .

## <a name="example"></a>Przykład

Poniższy przykład pokazuje,  **\<** jak używać elementu Remove > w pliku konfiguracyjnym aplikacji, aby usunąć ustawienia zdefiniowane wcześniej w pliku konfiguracji maszyny.

Poniższy kod pliku konfiguracji komputera deklaruje sekcję  **\<>** i `key1` dodaje dwa ustawienia i `key2`, do:

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

Następujący kod pliku konfiguracji aplikacji usuwa `key2` ustawienie z  **\<sekcji >** :

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
