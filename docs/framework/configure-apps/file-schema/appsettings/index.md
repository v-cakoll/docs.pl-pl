---
title: "Schemat ustawień aplikacji"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
helpviewer_keywords:
- schema app settings
- app settings, schema [Windows Forms]
- Windows Forms, app settings schema
- configuration schema [.NET Framework], app settings
ms.assetid: 99347d62-3ea5-40b6-bfec-c31431011422
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 1d51d06895e61be60bbe9153eacb2028cb32a1fa
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="app-settings-schema"></a>Schemat ustawień aplikacji

Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Dodaj >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md)   
&nbsp;&nbsp;&nbsp;&nbsp;[**\<Usuń >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md)

| Element | Opis |
| ------- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** znaczniki, aby kontrolować ustawienia aplikacji. Ma opcjonalny **pliku** atrybutu. |
| [**\<Dodaj >**](~/docs/framework/configure-apps/file-schema/appsettings/add-element-for-appsettings.md) | Definiuje ustawienie. Element podrzędny  **\<appSettings >**. Wymaga **klucza** i **wartość** atrybutów. |
| [**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/appsettings/clear-element-for-appsettings.md) | Czyści wszystkie ustawienia. Element podrzędny  **\<appSettings >**. Nie ma żadnych atrybutów. |
| [**\<Usuń >**](~/docs/framework/configure-apps/file-schema/appsettings/remove-element-for-appsettings.md) | Usuwa ustawienie. Element podrzędny  **\<appSettings >**. Wymaga **klucza** atrybutu. |

## <a name="appsettings-element"></a>\<appSettings > — element

Ten element zawiera  **\<Dodaj >**,  **\<Wyczyść >**, i  **\<Usuń >** znaczniki, aby kontrolować ustawienia aplikacji. Definiuje atrybut opcjonalny **pliku**.

## <a name="add-element"></a>\<Dodaj > — element

Dodaje ustawienie niestandardowej aplikacji jako pary nazwa/wartość w kolekcji ustawień aplikacji. Definiuje atrybuty **klucza** i **wartość**.

## <a name="clear-element"></a>\<Wyczyść > — element

Usuwa wszystkie odwołania do ustawienia dziedziczony niestandardową aplikację i umożliwia odwołań, które są dodawane przez  **\<Dodaj >** elementy następujące  **\<Wyczyść >** element. Definiuje żadnych atrybutów.

## <a name="remove-element"></a>\<Usuń > — element

Usuwa odwołanie do ustawienia dziedziczony niestandardową aplikację z kolekcji ustawień aplikacji. Definiuje atrybut **klucza**.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono plik ustawień zewnętrznej aplikacji (*custom.config*) definiuje ustawienia aplikacji niestandardowej:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<appSettings>
  <add key="MyCustomSetting" value="MyCustomSettingValue" />
</appSettings>
```

W poniższym przykładzie przedstawiono plik konfiguracji aplikacji, który wykorzystuje ustawienia w pliku ustawień zewnętrznych, a następnie ustawia ustawienie aplikacji z własnych:

```xml
<configuration>
  <appSettings file="custom.config">
    <add key="ApplicationName" value="MyApplication" />
  </appSettings>
</configuration>
```

## <a name="see-also"></a>Zobacz także

[Przegląd ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md)
