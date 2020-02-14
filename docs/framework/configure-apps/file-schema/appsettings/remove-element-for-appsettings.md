---
title: <remove>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
ms.openlocfilehash: 83abbdbf0d3e4dfd16c0e8c649200c4ecc7329f7
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215494"
---
# <a name="remove-element-for-appsettings"></a>\<usunąć > elementu \<appSettings >

Usuwa niestandardowe ustawienia aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<usuń >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atrybut

|         | Opis |
| ------- | ----------- |
| **Klucz** | Atrybut wymagany.<br><br>Określa nazwę klucza do usunięcia. |

### <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

None

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób usuwania niestandardowego ustawienia konfiguracji dla `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](../index.md)
