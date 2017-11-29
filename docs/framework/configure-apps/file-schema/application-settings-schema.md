---
title: "Schemat ustawień aplikacji"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
caps.latest.revision: "3"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: d93a18b17e0d6b8e413903fb84dc6b427d94f6af
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="application-settings-schema"></a>Schemat ustawień aplikacji

Ustawienia aplikacji pozwalają na przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika aplikacji formularzy systemu Windows lub programu ASP.NET. W tym kontekście *ustawienie* jest dowolne informacje, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko z ciągu połączenia bazy danych dla użytkownika preferowana przez domyślny rozmiar okna.

Domyślnie ustawienia aplikacji w aplikacji formularzy systemu Windows używa <xref:System.Configuration.LocalFileSettingsProvider> klasy, która przechowuje ustawienia w pliku konfiguracji XML przy użyciu systemu konfiguracji platformy .NET. Aby uzyskać więcej informacji na temat plików używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Ustawienia aplikacji definiuje następujące elementy jako część plików konfiguracyjnych, które są używane.

| Element                    | Opis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Zawiera wszystkie  **\<Ustawienia >** tagi specyficzne dla aplikacji.                         |
| **\<Ustawienia użytkownika >**        | Zawiera wszystkie  **\<Ustawienia >** tagi specyficzne dla bieżącego użytkownika.                        |
| **\<Ustawienia >**             | Definiuje ustawienie. Jeden element podrzędny  **\<applicationSettings >** lub  **\<ustawienia użytkownika >**. |
| **\<wartość >**               | Definiuje wartości ustawień. Element podrzędny  **\<Ustawienia >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > — element

Ten element zawiera wszystkie  **\<Ustawienia >** tagi, które są specyficzne dla wystąpienia aplikacji na komputerze klienckim. Definiuje żadnych atrybutów.

## <a name="usersettings-element"></a>\<Ustawienia użytkownika > — element

Ten element zawiera wszystkie  **\<Ustawienia >** tagi, które są specyficzne dla użytkownika, który jest obecnie przy użyciu aplikacji. Definiuje żadnych atrybutów.

## <a name="setting-element"></a>\<Ustawienia > — element

Ten element definiuje ustawienia. Ma ona następujące atrybuty.

| Atrybut        | Opis |
| ---------------- | ----------- |
| **Nazwa**         | Wymagany. Unikatowy identyfikator ustawienia. Ustawienia utworzone za pomocą programu Visual Studio są zapisywane o nazwie `ProjectName.Properties.Settings`. |
| **serializedAs** | Wymagany. Format używany do serializacji wartości Text. Prawidłowe wartości to:<br><br>- `string`. Wartość jest szeregowana jako parametry za pomocą <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Wartość jest serializowany za pomocą serializacji XML.<br>- `binary`. Wartość jest serializowany jako wartość binarną kodowany w formacie tekstowym za pomocą serializacji binarnej.<br />- `custom`. Dostawca ustawień ma nieodłącznej wiedzy o to ustawienie i serializuje i zwalnia wykonuje serializację. |

## <a name="value-element"></a>\<wartość > — element

Ten element zawiera wartości ustawienia.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono plik ustawień aplikacji, który definiuje dwa ustawienia zakresu aplikacji i dwa ustawienia zakresu użytkownika:

```xml
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <configSections>
    <sectionGroup name="applicationSettings" type="System.Configuration.ApplicationSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />
    </sectionGroup>
    <sectionGroup name="userSettings" type="System.Configuration.UserSettingsGroup, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">
      <section name="WindowsApplication1.Properties.Settings" type="System.Configuration.ClientSettingsSection, System, Version=2.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" allowExeDefinition="MachineToLocalUser" />
    </sectionGroup>
  </configSections>
  <applicationSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="Cursor" serializeAs="String">
        <value>Default</value>
      </setting>
      <setting name="DoubleBuffering" serializeAs="String">
        <value>False</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </applicationSettings>
  <userSettings>
    <WindowsApplication1.Properties.Settings>
      <setting name="FormTitle" serializeAs="String">
        <value>Form1</value>
      </setting>
      <setting name="FormSize" serializeAs="String">
        <value>595, 536</value>
      </setting>
    </WindowsApplication1.Properties.Settings>
  </userSettings>
</configuration>
```

## <a name="see-also"></a>Zobacz także

[Przegląd ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-overview.md)   
[Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md)
