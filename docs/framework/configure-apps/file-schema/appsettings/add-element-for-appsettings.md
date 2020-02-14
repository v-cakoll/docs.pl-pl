---
title: <add>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/add
helpviewer_keywords:
- add Element
- <add> Element
ms.assetid: 8734efdc-00f6-4a65-bba6-084c5bc65246
ms.openlocfilehash: 5c7de79ec626966e71d461dd3865b294a8979db2
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214816"
---
# <a name="add-element-for-appsettings"></a>\<dodać > elementu \<appSettings >

Dodaje niestandardowe ustawienie aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<dodaj >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <add key="Key of custom setting" value="Value of custom setting" />
</appSettings>
```

## <a name="attributes"></a>Atrybuty

|           | Opis |
| --------- | ----------- |
| **Klucz**   | Atrybut wymagany.<br><br>Określa nazwę klucza do dodania. |
| **value** | Atrybut wymagany.<br><br>Określa wartość klucza do dodania. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

None

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dodać niestandardowe ustawienie konfiguracji dla nazwy aplikacji:

```xml
<appSettings>
  <add key="ApplicationName" value="MyApplication" />
</appSettings>
```

Poniższy przykład używa elementu `<add>`, aby zdefiniować dwa ustawienia zgodności w aplikacji ASP.NET:

```xml
<appSettings>
  <add key="AppContext.SetSwitch:Switch.System.Globalization.NoAsyncCurrentCulture" value="true" />
  <add key="AppContext.SetSwitch:Switch.System.Uri.DontEnableStrictRFC3986ReservedCharacterSets" value="true" />
</appSettings>
```

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](../index.md)
