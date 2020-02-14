---
title: Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/sectionName
helpviewer_keywords:
- custom element
ms.assetid: 2303031f-4c1d-4df4-bca1-e9bd96ca40dc
ms.openlocfilehash: e5c5c6cf5744aa385e6f6700cad623751a4d7427
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215477"
---
# <a name="custom-element-for-namevaluesectionhandler-and-dictionarysectionhandler"></a>Element niestandardowy dla NameValueSectionHandler i DictionarySectionHandler

Definiuje ustawienia niestandardowych sekcji konfiguracji, które używają klas <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>.

[ **\<> konfiguracji**](configuration-element.md)\
&nbsp;&nbsp; **\<sectionname >**

## <a name="attributes"></a>Atrybuty

None

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **> konfiguracji \<** ](configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [ **\<dodać >** ](add-element-for-custom-2.md) dla <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler>  | Dodaje niestandardowe ustawienia aplikacji. |
| [ **\<usunąć >** ](remove-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> | Usuwa poprzednio zdefiniowane ustawienie. |
| [ **\<wyczyść >** ](clear-element-for-custom-2.md) <xref:System.Configuration.NameValueSectionHandler> i <xref:System.Configuration.DictionarySectionHandler> | Czyści wszystkie poprzednio zdefiniowane ustawienia w sekcji. |

## <a name="remarks"></a>Uwagi

**\<sectionname >** element jest elementem niestandardowym zdefiniowanym przez **\<sekcję >** tagu w\<elementu > **configSections** .

W poniższej tabeli przedstawiono typ obiektu, który zwraca metoda ConfigurationSettings. GetConfig dla każdej procedury obsługi sekcji konfiguracji:

| Procedura obsługi sekcji konfiguracji                        | Zwracany typ                                                |
| ---------------------------------------------------- | ---------------------------------------------------------- |
| <xref:System.Configuration.NameValueSectionHandler>  | <xref:System.Collections.Specialized.NameValueCollection>  |
| <xref:System.Configuration.DictionarySectionHandler> | <xref:System.Collections.IDictionary>                      |

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować sekcje, które używają klas <xref:System.Configuration.DictionarySectionHandler> i <xref:System.Configuration.NameValueSectionHandler>.

Pierwszy element niestandardowy jest **\<dictionarySample >** , który zawiera ustawienia odczytane przez klasę <xref:System.Configuration.DictionarySectionHandler> w zestawie `System.dll`. Drugi element niestandardowy jest **\<sekcji >** , która zawiera ustawienia odczytane przez klasę <xref:System.Configuration.NameValueSectionHandler> w zestawie `System.dll`.

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

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](index.md)
