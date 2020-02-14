---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
ms.openlocfilehash: 266d32ccb8b322f0472e0f552f9c0fc877c9a78e
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77214798"
---
# <a name="clear-element-for-appsettings"></a>\<Wyczyść > elementu \<appSettings >

Czyści niestandardowe ustawienia aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Atrybuty

None

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

None

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Zobacz też

- [Schemat pliku konfiguracji dla .NET Framework](../index.md)
