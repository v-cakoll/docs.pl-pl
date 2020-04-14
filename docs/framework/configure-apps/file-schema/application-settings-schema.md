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
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242832"
---
# <a name="application-settings-schema"></a>Schemat ustawień aplikacji

Ustawienia aplikacji umożliwiają aplikacji Windows Forms lub ASP.NET do przechowywania i pobierania ustawień o zakresie aplikacji i o zakresie użytkownika. W tym kontekście *ustawienie* jest wszelkie informacje, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko od ciągu połączenia bazy danych do preferowanego domyślnego rozmiaru okna użytkownika.

Domyślnie ustawienia aplikacji w aplikacji Windows <xref:System.Configuration.LocalFileSettingsProvider> Forms używają tej klasy, która używa systemu konfiguracji platformy .NET do przechowywania ustawień w pliku konfiguracyjnym XML. Aby uzyskać więcej informacji o plikach używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md).

Ustawienia aplikacji definiuje następujące elementy jako część plików konfiguracyjnych, których używa.

| Element                    | Opis                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<aplikacjaRozstawy>** | Zawiera wszystkie ** \<znaczniki>ustawień** specyficzne dla aplikacji.                         |
| **\<>użytkowników**        | Zawiera wszystkie ** \<znaczniki>ustawień** specyficzne dla bieżącego użytkownika.                        |
| **\<ustawianie>**             | Definiuje ustawienie. Dziecko albo ** \<applicationSettings>** lub ** \<userSettings>**. |
| **\<wartość>**               | Definiuje wartość ustawienia. Podrzędny ** \<ustawienie>**.                                   |

## <a name="applicationsettings-element"></a>\<applicationSettings> element

Ten element zawiera wszystkie ** \<znaczniki>ustawień,** które są specyficzne dla wystąpienia aplikacji na komputerze klienckim. Definiuje żadnych atrybutów.

## <a name="usersettings-element"></a>\<userSettings> element

Ten element ** \<** zawiera wszystkie ustawienia>tagów, które są specyficzne dla użytkownika, który aktualnie korzysta z aplikacji. Definiuje żadnych atrybutów.

## <a name="setting-element"></a>\<ustawienie elementu>

Ten element definiuje ustawienie. Ma następujące atrybuty.

| Atrybut        | Opis |
| ---------------- | ----------- |
| **Nazwa**         | Wymagany. Unikatowy identyfikator ustawienia. Ustawienia utworzone za pomocą programu `ProjectName.Properties.Settings`Visual Studio są zapisywane z nazwą . |
| **serializeAs** | Wymagany. Format używany do serializacji wartości do tekstu. Prawidłowe wartości:<br><br>- `string`. Wartość jest serializowana jako <xref:System.ComponentModel.TypeConverter>ciąg przy użyciu pliku .<br>- `xml`. Wartość jest serializowana przy użyciu serializacji XML.<br>- `binary`. Wartość jest serializowana jako plik binarny zakodowany w tekście przy użyciu serializacji binarnej.<br />- `custom`. Dostawca ustawień ma wrodzoną wiedzę na temat tego ustawienia i serializuje i de-serializuje go. |

## <a name="value-element"></a>\<wartość> element

Ten element zawiera wartość ustawienia.

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano plik ustawień aplikacji, który definiuje dwa ustawienia o zakresie aplikacji i dwa ustawienia o zakresie użytkownika:

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

## <a name="see-also"></a>Zobacz też

- [Przegląd ustawień aplikacji](../../winforms/advanced/application-settings-overview.md)
- [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md)
