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
# <a name="application-settings-schema"></a><span data-ttu-id="740d9-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="740d9-102">Application Settings schema</span></span>

<span data-ttu-id="740d9-103">Ustawienia aplikacji umożliwiają aplikacji Windows Forms lub ASP.NET do przechowywania i pobierania ustawień o zakresie aplikacji i o zakresie użytkownika.</span><span class="sxs-lookup"><span data-stu-id="740d9-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="740d9-104">W tym kontekście *ustawienie* jest wszelkie informacje, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko od ciągu połączenia bazy danych do preferowanego domyślnego rozmiaru okna użytkownika.</span><span class="sxs-lookup"><span data-stu-id="740d9-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="740d9-105">Domyślnie ustawienia aplikacji w aplikacji Windows <xref:System.Configuration.LocalFileSettingsProvider> Forms używają tej klasy, która używa systemu konfiguracji platformy .NET do przechowywania ustawień w pliku konfiguracyjnym XML.</span><span class="sxs-lookup"><span data-stu-id="740d9-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="740d9-106">Aby uzyskać więcej informacji o plikach używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="740d9-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="740d9-107">Ustawienia aplikacji definiuje następujące elementy jako część plików konfiguracyjnych, których używa.</span><span class="sxs-lookup"><span data-stu-id="740d9-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="740d9-108">Element</span><span class="sxs-lookup"><span data-stu-id="740d9-108">Element</span></span>                    | <span data-ttu-id="740d9-109">Opis</span><span class="sxs-lookup"><span data-stu-id="740d9-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="740d9-110">**\<aplikacjaRozstawy>**</span><span class="sxs-lookup"><span data-stu-id="740d9-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="740d9-111">Zawiera wszystkie \*\* \<znaczniki>ustawień\*\* specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="740d9-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="740d9-112">**\<>użytkowników**</span><span class="sxs-lookup"><span data-stu-id="740d9-112">**\<userSettings>**</span></span>        | <span data-ttu-id="740d9-113">Zawiera wszystkie \*\* \<znaczniki>ustawień\*\* specyficzne dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="740d9-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="740d9-114">**\<ustawianie>**</span><span class="sxs-lookup"><span data-stu-id="740d9-114">**\<setting>**</span></span>             | <span data-ttu-id="740d9-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="740d9-115">Defines a setting.</span></span> <span data-ttu-id="740d9-116">Dziecko albo \*\* \<applicationSettings>\*\* lub \*\* \<userSettings>\*\*.</span><span class="sxs-lookup"><span data-stu-id="740d9-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="740d9-117">**\<wartość>**</span><span class="sxs-lookup"><span data-stu-id="740d9-117">**\<value>**</span></span>               | <span data-ttu-id="740d9-118">Definiuje wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="740d9-118">Defines a setting's value.</span></span> <span data-ttu-id="740d9-119">Podrzędny \*\* \<ustawienie>\*\*.</span><span class="sxs-lookup"><span data-stu-id="740d9-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="740d9-120">\<applicationSettings> element</span><span class="sxs-lookup"><span data-stu-id="740d9-120">\<applicationSettings> element</span></span>

<span data-ttu-id="740d9-121">Ten element zawiera wszystkie \*\* \<znaczniki>ustawień,\*\* które są specyficzne dla wystąpienia aplikacji na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="740d9-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="740d9-122">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="740d9-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="740d9-123">\<userSettings> element</span><span class="sxs-lookup"><span data-stu-id="740d9-123">\<userSettings> element</span></span>

<span data-ttu-id="740d9-124">Ten element \*\* \<\*\* zawiera wszystkie ustawienia>tagów, które są specyficzne dla użytkownika, który aktualnie korzysta z aplikacji.</span><span class="sxs-lookup"><span data-stu-id="740d9-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="740d9-125">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="740d9-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="740d9-126">\<ustawienie elementu></span><span class="sxs-lookup"><span data-stu-id="740d9-126">\<setting> element</span></span>

<span data-ttu-id="740d9-127">Ten element definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="740d9-127">This element defines a setting.</span></span> <span data-ttu-id="740d9-128">Ma następujące atrybuty.</span><span class="sxs-lookup"><span data-stu-id="740d9-128">It has the following attributes.</span></span>

| <span data-ttu-id="740d9-129">Atrybut</span><span class="sxs-lookup"><span data-stu-id="740d9-129">Attribute</span></span>        | <span data-ttu-id="740d9-130">Opis</span><span class="sxs-lookup"><span data-stu-id="740d9-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="740d9-131">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="740d9-131">**name**</span></span>         | <span data-ttu-id="740d9-132">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="740d9-132">Required.</span></span> <span data-ttu-id="740d9-133">Unikatowy identyfikator ustawienia.</span><span class="sxs-lookup"><span data-stu-id="740d9-133">The unique ID of the setting.</span></span> <span data-ttu-id="740d9-134">Ustawienia utworzone za pomocą programu `ProjectName.Properties.Settings`Visual Studio są zapisywane z nazwą .</span><span class="sxs-lookup"><span data-stu-id="740d9-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="740d9-135">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="740d9-135">**serializeAs**</span></span> | <span data-ttu-id="740d9-136">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="740d9-136">Required.</span></span> <span data-ttu-id="740d9-137">Format używany do serializacji wartości do tekstu.</span><span class="sxs-lookup"><span data-stu-id="740d9-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="740d9-138">Prawidłowe wartości:</span><span class="sxs-lookup"><span data-stu-id="740d9-138">Valid values are:</span></span><br><br><span data-ttu-id="740d9-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="740d9-139">- `string`.</span></span> <span data-ttu-id="740d9-140">Wartość jest serializowana jako <xref:System.ComponentModel.TypeConverter>ciąg przy użyciu pliku .</span><span class="sxs-lookup"><span data-stu-id="740d9-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="740d9-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="740d9-141">- `xml`.</span></span> <span data-ttu-id="740d9-142">Wartość jest serializowana przy użyciu serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="740d9-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="740d9-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="740d9-143">- `binary`.</span></span> <span data-ttu-id="740d9-144">Wartość jest serializowana jako plik binarny zakodowany w tekście przy użyciu serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="740d9-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="740d9-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="740d9-145">- `custom`.</span></span> <span data-ttu-id="740d9-146">Dostawca ustawień ma wrodzoną wiedzę na temat tego ustawienia i serializuje i de-serializuje go.</span><span class="sxs-lookup"><span data-stu-id="740d9-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="740d9-147">\<wartość> element</span><span class="sxs-lookup"><span data-stu-id="740d9-147">\<value> element</span></span>

<span data-ttu-id="740d9-148">Ten element zawiera wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="740d9-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="740d9-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="740d9-149">Example</span></span>

<span data-ttu-id="740d9-150">W poniższym przykładzie pokazano plik ustawień aplikacji, który definiuje dwa ustawienia o zakresie aplikacji i dwa ustawienia o zakresie użytkownika:</span><span class="sxs-lookup"><span data-stu-id="740d9-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="740d9-151">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="740d9-151">See also</span></span>

- [<span data-ttu-id="740d9-152">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="740d9-152">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="740d9-153">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="740d9-153">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
