---
title: Schemat ustawień aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
author: mcleblanc
ms.author: markl
ms.openlocfilehash: f11be59941759687806591feb1edcce28b2119e6
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123341"
---
# <a name="application-settings-schema"></a>Schemat ustawień aplikacji

Ustawienia aplikacji umożliwiają aplikacji Windows Forms i ASP.NET do przechowywania i pobierania ustawień o zakresie aplikacji i zakresie użytkownika. W tym kontekście *ustawienie* jest dowolne informacje, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — od ciąg połączenia bazy danych dla użytkownika preferowanego domyślny rozmiar okna.

Domyślnie używa ustawienia aplikacji w aplikacji Windows Forms <xref:System.Configuration.LocalFileSettingsProvider> klasy, która używa systemu konfiguracji platformy .NET do przechowywania ustawień w pliku konfiguracji XML. Aby uzyskać więcej informacji na temat plików używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md).

Ustawienia aplikacji definiuje następujące elementy w ramach plików konfiguracyjnych, które są używane.

| Element                    | Opis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings >** | Zawiera wszystkie  **\<Ustawienia >** tagi dotyczące tej aplikacji.                         |
| **\<Ustawienia użytkownika >**        | Zawiera wszystkie  **\<Ustawienia >** tagi specyficzne dla bieżącego użytkownika.                        |
| **\<Ustawienia >**             | Definiuje ustawienie. Element podrzędny elementu albo  **\<applicationSettings >** lub  **\<ustawienia użytkownika >**. |
| **\<wartość >**               | Określa wartość tego ustawienia. Element podrzędny elementu  **\<Ustawienia >**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings > element

Ten element zawiera wszystkie  **\<Ustawienia >** znaczniki, które są właściwe dla danego wystąpienia aplikacji na komputerze klienckim. Definiuje żadnych atrybutów.

## <a name="usersettings-element"></a>\<Ustawienia użytkownika > element

Ten element zawiera wszystkie  **\<Ustawienia >** tagi, które są specyficzne dla użytkownika, który jest obecnie przy użyciu aplikacji. Definiuje żadnych atrybutów.

## <a name="setting-element"></a>\<Ustawienia > element

Ten element definiuje ustawienia. Ma następujące atrybuty.

| Atrybut        | Opis |
| ---------------- | ----------- |
| **Nazwa**         | Wymagane. Unikatowy identyfikator ustawienia. Ustawień utworzonych za pomocą programu Visual Studio są zapisywane razem z nazwą `ProjectName.Properties.Settings`. |
| **serializedAs** | Wymagane. Format używany do serializacji wartości do tekstu. Prawidłowe wartości to:<br><br>- `string`. Wartość jest serializowany jako ciąg za pośrednictwem <xref:System.ComponentModel.TypeConverter>.<br>- `xml`. Wartość jest serializowana, za pomocą serializacji XML.<br>- `binary`. Wartość jest serializowany jako dane binarne zakodowane w formacie tekstowym, za pomocą serializacji binarnej.<br />- `custom`. Dostawca ustawień ma nieodłącznej wiedzy o ustawienie serializuje i deserializuje go. |

## <a name="value-element"></a>\<wartość > element

Ten element zawiera wartości ustawienia.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje plik ustawień aplikacji, który definiuje dwa ustawienia w zakresie aplikacji i dwóch ustawień zakresu użytkownika:

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
