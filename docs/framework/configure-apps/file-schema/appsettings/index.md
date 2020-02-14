---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
ms.openlocfilehash: 0a3363b35a6fc8bd27753eb034f8a1e95feb5292
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77215428"
---
# <a name="app-settings-schema"></a>Schemat ustawień aplikacji

Zawiera niestandardowe ustawienia aplikacji, takie jak ścieżki plików, adresy URL usług sieci Web XML lub inne niestandardowe informacje o konfiguracji dla aplikacji.

[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<appSettings >** ](appsettings-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dodaj >** ](add-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<wyczyść >** ](clear-element-for-appsettings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Usuń >** ](remove-element-for-appsettings.md)

| Element | Opis |
| ------- | ----------- |
| [ **\<appSettings >** ](appsettings-element-for-configuration.md) | Zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji. Ma opcjonalny atrybut **pliku** . |
| [ **\<Dodaj >** ](add-element-for-appsettings.md) | Definiuje ustawienie. Element podrzędny **>\<AppSettings**. Wymaga atrybutów **klucza** i **wartości** . |
| [ **\<Wyczyść >** ](clear-element-for-appsettings.md) | Czyści wszystkie ustawienia. Element podrzędny **>\<AppSettings**. Nie ma atrybutów. |
| [ **\<Usuń >** ](remove-element-for-appsettings.md) | Usuwa ustawienie. Element podrzędny **>\<AppSettings**. Wymaga atrybutu **klucza** . |

## <a name="appsettings-element"></a>\<appSettings > element

Ten element zawiera **\<dodaj >** , **\<wyczyść >** i **\<Usuń Tagi >** w celu kontrolowania ustawień aplikacji. Definiuje opcjonalny atrybut dla **pliku**.

## <a name="add-element"></a>\<dodać elementu >

Dodaje niestandardowe ustawienie aplikacji jako parę nazwa/wartość do kolekcji ustawień aplikacji. Definiuje atrybuty **klucza** i **wartości**.

## <a name="clear-element"></a>\<Wyczyść > elementu

Usuwa wszystkie odwołania do dziedziczonych ustawień aplikacji niestandardowych i zezwala tylko na odwołania, które są dodawane przez **\<dodaj >** elementy po **\<Wyczyść >** elementu. Nie definiuje żadnych atrybutów.

## <a name="remove-element"></a>\<usunąć elementu >

Usuwa odwołanie do dziedziczonego ustawienia aplikacji niestandardowej z kolekcji ustawień aplikacji. Definiuje atrybut dla **klucza**.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono zewnętrzny plik ustawień aplikacji (*Custom. config*) definiujący niestandardowe ustawienie aplikacji:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Poniższy przykład przedstawia plik konfiguracji aplikacji, który używa ustawienia w pliku ustawień zewnętrznych i ustawia własne ustawienie aplikacji:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Zobacz też

- [Przegląd ustawień aplikacji](../../../winforms/advanced/application-settings-overview.md)
- [Architektura ustawień aplikacji](../../../winforms/advanced/application-settings-architecture.md)
