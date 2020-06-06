---
title: Schemat ustawień aplikacji
ms.date: 03/30/2017
helpviewer_keywords:
- schema application settings
- application settings, schema [Windows Forms]
- Windows Forms, application settings schema
- configuration schema [.NET Framework], application settings
ms.assetid: 5797fcff-6081-4e8c-bebf-63d9c70cf14b
ms.openlocfilehash: 90d471888950347c041b4824b659ce33fda512d7
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "81242832"
---
# <a name="application-settings-schema"></a>Schemat ustawień aplikacji

Ustawienia aplikacji zezwalają aplikacji Windows Forms lub ASP.NET na przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika. W tym kontekście *ustawienie* jest dowolnymi informacjami, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko to w parametrach połączenia bazy danych do preferowanego domyślnego rozmiaru okna użytkownika.

Domyślnie ustawienia aplikacji w aplikacji Windows Forms używają <xref:System.Configuration.LocalFileSettingsProvider> klasy, która używa systemu konfiguracji platformy .NET do przechowywania ustawień w pliku konfiguracyjnym XML. Aby uzyskać więcej informacji na temat plików używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md).

Ustawienia aplikacji definiują następujące elementy w ramach używanych plików konfiguracji.

| Element                    | Opis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | Zawiera wszystkie **\<setting>** znaczniki specyficzne dla aplikacji.                         |
| **\<userSettings>**        | Zawiera wszystkie **\<setting>** znaczniki specyficzne dla bieżącego użytkownika.                        |
| **\<setting>**             | Definiuje ustawienie. Element podrzędny jednego **\<applicationSettings>** lub **\<userSettings>** . |
| **\<value>**               | Definiuje wartość ustawienia. Element podrzędny **\<setting>** .                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings>, element

Ten element zawiera wszystkie **\<setting>** Tagi, które są specyficzne dla wystąpienia aplikacji na komputerze klienckim. Nie definiuje żadnych atrybutów.

## <a name="usersettings-element"></a>\<userSettings>, element

Ten element zawiera wszystkie **\<setting>** Tagi, które są specyficzne dla użytkownika, który aktualnie używa aplikacji. Nie definiuje żadnych atrybutów.

## <a name="setting-element"></a>\<setting>, element

Ten element definiuje ustawienie. Ma następujące atrybuty.

| Atrybut        | Opis |
| ---------------- | ----------- |
| **Nazwij**         | Wymagany. Unikatowy identyfikator ustawienia. Ustawienia utworzone za pomocą programu Visual Studio są zapisywane z nazwą `ProjectName.Properties.Settings` . |
| **serializeAs** | Wymagany. Format służący do serializowania wartości do tekstu. Prawidłowe wartości:<br><br>- `string`. Wartość jest serializowana jako ciąg za pomocą <xref:System.ComponentModel.TypeConverter> .<br>- `xml`. Wartość jest serializowana przy użyciu serializacji XML.<br>- `binary`. Wartość jest serializowana jako plik binarny kodowany tekstem przy użyciu serializacji binarnej.<br />- `custom`. Dostawca ustawień ma nieodłączną wiedzę o tym ustawieniu i serializować i deserializacji. |

## <a name="value-element"></a>\<value>, element

Ten element zawiera wartość ustawienia.

## <a name="example"></a>Przykład

W poniższym przykładzie przedstawiono plik ustawień aplikacji, który definiuje dwa ustawienia dotyczące zakresu aplikacji i dwa ustawienia o zakresie użytkownika:

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

- [Przegląd ustawień aplikacji](../../winforms/advanced/application-settings-overview.md)
- [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md)
