---
title: '&lt;sectionGroup&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/sectionGroup
helpviewer_keywords:
- sectionGroup Element
- <sectionGroup> Element
ms.assetid: 6c27f9e2-809c-4bc9-aca9-72f90360e7a3
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5c5c040a322c38da319f2e964519f94d761327e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="sectiongroup-element-for-configsections"></a>\<sectionGroup > elementu \<configSections >

Definiuje obszar nazw dla sekcji konfiguracyjnych.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<sectionGroup >**

## <a name="syntax"></a>Składnia

```xml
<sectionGroup name="section group name">
  <!-- Configuration sections -->
</sectionGroup>
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Nazwa**  | Atrybut wymagany.<br><br>Określa nazwę grupy sekcji definiowanej. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<configSections >** — Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Zawiera konfigurację deklaracji sekcji i przestrzeni nazw. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<sekcja >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Zawiera deklaracji sekcji konfiguracji. |

## <a name="remarks"></a>Uwagi

Deklarowanie grupy sekcji tworzy znacznik sekcji konfiguracji i zapewnia, że nie ma żadnych konfliktów nazw z sekcji konfiguracyjnych, zdefiniowana przez kogoś innego. Można zagnieżdżać  **\<sectionGroup >** elementy wewnątrz innych.

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób zadeklarować grupy sekcji ani deklarować sekcje w obrębie grupy sekcji:

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

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
