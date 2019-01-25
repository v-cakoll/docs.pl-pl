---
title: '&lt;Usuń&gt; elementu &lt;configSections&gt;'
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 5e105cbfe0c6db2b9157134ee32c1b353ec794fd
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596513"
---
# <a name="remove-element-for-configsections"></a>\<Usuń >, element dla \<configSections >

Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<remove>**

## <a name="syntax"></a>Składnia

```xml
<remove name="section name or section group name" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Nazwa**  | Atrybut wymagany.<br><br>Określa nazwę sekcji lub grupy sekcji do usunięcia. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<configSections>** Element](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Możesz użyć  **\<Usuń >** elementu do usunięcia sekcje i grup sekcji z poziomu aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać  **\<Usuń >** elementu w pliku konfiguracyjnym aplikacji, aby usunąć sekcję wcześniej zdefiniowane w pliku konfiguracji komputera.

Poniższy kod pliku konfiguracji maszyny deklaruje sekcji  **\<sampleSection >**:

```xml
<!-- Machine.config file -->
<configuration>
  <configSections>
    <section name="sampleSection"
             type="System.Configuration.SingleTagSectionHandler" />
  </configSections>
  <sampleSection setting1="Value1" 
                 setting2="value two" 
                 setting3="third value" />
</configuration>
```

Poniższy kod pliku konfiguracji aplikacji usuwa  **\<sampleSection >** sekcji. Po usunięciu aplikacji nie można pobrać ustawień w  **\<sampleSection >**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji, plik konfiguracji komputera (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
