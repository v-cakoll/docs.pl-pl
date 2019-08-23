---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 890269857aaa00ce62195ccb2f4cb184b363b61e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921042"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler

Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają <xref:System.Configuration.NameValueSectionHandler> klas i. <xref:System.Configuration.DictionarySectionHandler>

[ **\<> konfiguracji**](configuration-element.md)\
&nbsp;&nbsp; **\<sectionName>**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<> konfiguracji**](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| Dodaj > dla i [ **\<** ](add-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler>  | Dodaje niestandardowe ustawienia aplikacji. |
| Usuń > dla i [ **\<** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler> | Usuwa poprzednio zdefiniowane ustawienie. |
| Wyczyść > dla i [ **\<** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler><xref:System.Configuration.DictionarySectionHandler> | Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji. |

## <a name="remarks"></a>Uwagi

**\<Parametrami sectionName>** element jest elementem niestandardowe zdefiniowane przez **\<sekcji>** tagów w **\<configSections>** elementu.

W poniższej tabeli przedstawiono typ obiektu, który zwraca metoda ConfigurationSettings. GetConfig dla każdej procedury obsługi sekcji konfiguracji:

| Procedura obsługi sekcji konfiguracji                        | Typ zwracany                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować sekcje, które używają <xref:System.Configuration.DictionarySectionHandler> klas <xref:System.Configuration.NameValueSectionHandler> i.

Pierwszy element niestandardowy to  **\<dictionarySample >** , który zawiera <xref:System.Configuration.DictionarySectionHandler> ustawienia odczytane przez klasę w `System.dll` zestawie. Drugi element niestandardowy jest  **\<częścią >** , która zawiera <xref:System.Configuration.NameValueSectionHandler> ustawienia odczytane przez klasę w `System.dll` zestawie.

```xml
<configuration>
  <configSections>
    <section name="dictionarySample" type="System.Configuration.DictionarySectionHandler,System" />
    <sectionGroup name="mySectionGroup">
      <section name="mySection" type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
  <dictionarySample>
    <add key="myKey" value="myValue" />
  </dictionarySample>
  <mySectionGroup>
    <mySection>
      <add key="key1" value="value1" />
    </mySection>
  </mySectionGroup>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Tego elementu można użyć w pliku konfiguracyjnym aplikacji, pliku konfiguracji komputera (*Machine. config*) i plikach *Web. config* , które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
