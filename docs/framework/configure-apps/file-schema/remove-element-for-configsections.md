---
title: <remove>, element dla <configSections>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/configSections/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: ae4d82e0-e8fe-468c-81ab-46d63c4d66a8
ms.openlocfilehash: 6991e3f73ac180fc690ec48e1a0d15f40c915733
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154533"
---
# <a name="remove-element-for-configsections"></a>\<usunąć element> \<dla konfisek>

Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.

[**\<>konfiguracyjne**](configuration-element.md)\
&nbsp;&nbsp;[**\<>konfiguracyjne**](configsections-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<usuń>**

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
| [** \<configSekcje>** Element](configsections-element-for-configuration.md) | Zawiera sekcje konfiguracji i deklaracje obszaru nazw. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

Można użyć ** \<elementu>usuwania,** aby usunąć sekcje i grupy sekcji z aplikacji, które zostały zdefiniowane na wyższym poziomie w hierarchii plików konfiguracji.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak użyć elementu ** \<>w** pliku konfiguracji aplikacji, aby usunąć sekcję wcześniej zdefiniowaną w pliku konfiguracji komputera.

Następujący kod pliku konfiguracji maszyny deklaruje ** \<przykład sekcjiSekcja>: **

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

Poniższy kod pliku konfiguracji aplikacji usuwa ** \<przykładową sekcję>.** Po usunięciu aplikacja nie może pobrać ustawień w ** \<próbceSekcja>**.

```xml
<!-- Application configuration file -->
<configuration>
  <configSections>
    <remove name="sampleSection"/>
  </configSections>
</configuration>
```

## <a name="configuration-file"></a>Plik konfiguracji

Ten element może być używany w pliku konfiguracyjnym aplikacji, pliku konfiguracyjnym komputera *(Machine.config)* i plikach *Web.config,* które nie znajdują się na poziomie katalogu aplikacji.

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracyjnego programu .NET Framework](index.md)
