---
title: <clear>, element dla <appSettings>
ms.date: 05/01/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/clear
helpviewer_keywords:
- clear Element
- <clear> Element
ms.assetid: 6d18c7be-27db-438b-8fb5-765d396b0b7b
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 5d5da531bff3a0e9e198ba9b5ab6cf2b52bf36b5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921317"
---
# <a name="clear-element-for-appsettings"></a>\<Wyczyść > element dla \<AppSettings >

Czyści niestandardowe ustawienia aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)   
&nbsp;&nbsp;[ **\<appSettings>** ](appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<clear>**

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
| [ **\<appSettings>** ](appsettings-element-for-configuration.md) | Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji aplikacji. |

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
