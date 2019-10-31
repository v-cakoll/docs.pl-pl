---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c3e1c3a3cfd61a9fa8e7abdae9a25ec1bc674492
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73119228"
---
# <a name="clear-element-for-appsettings"></a>\<Wyczyść > elementu \<appSettings >

Czyści niestandardowe ustawienia aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<wyczyść >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="attributes"></a>Atrybuty

Brak

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak wyczyścić niestandardowe ustawienia konfiguracji:

```xml
<appSettings>
  <clear />
</appSettings>
```

## <a name="see-also"></a>Zobacz także

- [Schemat pliku konfiguracji dla .NET Framework](../index.md)
