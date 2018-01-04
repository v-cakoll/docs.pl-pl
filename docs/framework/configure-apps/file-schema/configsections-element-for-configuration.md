---
title: '&lt;configSections&gt; elementu &lt;konfiguracji&gt;'
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections
helpviewer_keywords:
- configSections Element
- <configSections> Element
ms.assetid: 9f963c1b-dc3f-4220-a8b6-2dd7a5a8e039
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 145a2a5cc23758c9fd2211c2da7fee0bbd736f0f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configsections-element-for-configuration"></a>\<configSections > elementu \<configuration >

Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;**\<configSections >**

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |

## <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<sekcja >**](~/docs/framework/configure-apps/file-schema/section-element.md) | Zawiera deklaracji sekcji konfiguracji. |
| [**\<sectionGroup >**](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | Definiuje obszar nazw dla sekcji konfiguracyjnych. |
| [**\<Usuń >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji. |
| [**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji. |

## <a name="remarks"></a>Uwagi

W przypadku tego elementu w pliku konfiguracji, musi być pierwszym elementem podrzędnym  **\<konfiguracji >** elementu.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak planować sekcji konfiguracji i określać ustawienia dla tej sekcji:

```xml
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

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być użyty w pliku konfiguracyjnym aplikacji plik konfiguracji maszyny (*Machine.config*), a *Web.config* pliki, które nie są na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
