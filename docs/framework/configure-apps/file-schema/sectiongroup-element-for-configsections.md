---
title: <sectionGroup>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
ms.openlocfilehash: eb221027470fe6e485f8fcc4b939b71e4f219712
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215260"
---
# <a name="sectiongroup-element-for-configsections"></a>\<> elementu \<configSections >

Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.

[ **\<> konfiguracji**](configuration-element.md)\
&nbsp;&nbsp;[ **\<configSections >** ](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<sekcji >**

## <a name="syntax"></a>Składnia

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Nazwij**  | Atrybut wymagany.<br><br>Określa nazwę definiowanej grupy sekcji. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<configSections >** Postaci](configsections-element-for-configuration.md) | Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [ **\<sekcja >** ](section-element.md) | Zawiera deklarację sekcji konfiguracyjnej. |

## <a name="remarks"></a>Uwagi

Deklarowanie grupy sekcji tworzy tag kontenera dla sekcji konfiguracyjnych i zapewnia, że nie występują konflikty nazw z sekcjami konfiguracji zdefiniowanymi przez kogoś innego. \<można zagnieżdżać **>** elementów w obrębie siebie.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować grupę sekcji i zadeklarować sekcje w grupie sekcji:

```xml
<configuration>
  <configSections>
    <sectionGroup name="mySectionGroup">
      <section name="mySection"
               type="System.Configuration.NameValueSectionHandler,System" />
    </sectionGroup>
  </configSections>
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
