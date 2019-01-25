---
title: Schemat ustawień aplikacji
ms.date: 05/01/2017
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
ms.openlocfilehash: 548d93e5447c06480629658b13b673aa3d15fc86
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620373"
---
# <a name="app-settings-schema"></a>Schemat ustawień aplikacji

Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki do plików, adresy URL usługi sieci Web XML lub inne informacje konfiguracji niestandardowej dla aplikacji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Element | Opis |
| ------- | ----------- |
| [**\<appSettings>**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** tagów, aby kontrolować ustawienia aplikacji. Ma opcjonalny **pliku** atrybutu. |
| [**\<add>**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Definiuje ustawienie. Element podrzędny elementu  **\<appSettings >**. Wymaga **klucz** i **wartość** atrybutów. |
| [**\<clear>**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Czyści wszystkie ustawienia. Element podrzędny elementu  **\<appSettings >**. nie ma żadnych atrybutów. |
| [**\<remove>**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Usuwa ustawienie. Element podrzędny elementu  **\<appSettings >**. Wymaga **klucz** atrybutu. |

## <a name="appsettings-element"></a>\<appSettings > element

Ten element zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** tagów, aby kontrolować ustawienia aplikacji. Definiuje on opcjonalny atrybut **pliku**.

## <a name="add-element"></a>\<Dodaj > element

Ustawienia niestandardowych aplikacji jako pary nazwa/wartość są dodawane do kolekcji ustawień aplikacji. Definiuje atrybuty **klucz** i **wartość**.

## <a name="clear-element"></a>\<Wyczyść > element

Usuwa wszystkie odwołania do ustawień dziedziczonych niestandardowych aplikacji i umożliwia tylko odwołań, które są dodawane przez  **\<Dodaj >** elementy następujące  **\<Wyczyść >** element. Definiuje żadnych atrybutów.

## <a name="remove-element"></a>\<Usuń > element

Usuwa odwołanie do ustawienia dziedziczone niestandardową aplikację z kolekcji ustawień aplikacji. Definiuje atrybut **klucz**.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje plik ustawień aplikacji zewnętrznej (*custom.config*) definiuje ustawienia aplikacji niestandardowej:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

Poniższy przykład przedstawia plik konfiguracji aplikacji, który wykorzystuje ustawienie w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji własnych:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [Przegląd ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-overview.md)
- [Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md)
