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
# <a name="application-settings-schema"></a><span data-ttu-id="a7eba-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7eba-102">Application Settings schema</span></span>

<span data-ttu-id="a7eba-103">Ustawienia aplikacji zezwalają aplikacji Windows Forms lub ASP.NET na przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7eba-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="a7eba-104">W tym kontekście *ustawienie* jest dowolnymi informacjami, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko to w parametrach połączenia bazy danych do preferowanego domyślnego rozmiaru okna użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7eba-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="a7eba-105">Domyślnie ustawienia aplikacji w aplikacji Windows Forms używają <xref:System.Configuration.LocalFileSettingsProvider> klasy, która używa systemu konfiguracji platformy .NET do przechowywania ustawień w pliku konfiguracyjnym XML.</span><span class="sxs-lookup"><span data-stu-id="a7eba-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="a7eba-106">Aby uzyskać więcej informacji na temat plików używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](../../winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="a7eba-106">For more information about the files used by application settings, see [Application Settings Architecture](../../winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="a7eba-107">Ustawienia aplikacji definiują następujące elementy w ramach używanych plików konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="a7eba-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="a7eba-108">Element</span><span class="sxs-lookup"><span data-stu-id="a7eba-108">Element</span></span>                    | <span data-ttu-id="a7eba-109">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eba-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| **\<applicationSettings>** | <span data-ttu-id="a7eba-110">Zawiera wszystkie **\<setting>** znaczniki specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7eba-110">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| **\<userSettings>**        | <span data-ttu-id="a7eba-111">Zawiera wszystkie **\<setting>** znaczniki specyficzne dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="a7eba-111">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| **\<setting>**             | <span data-ttu-id="a7eba-112">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a7eba-112">Defines a setting.</span></span> <span data-ttu-id="a7eba-113">Element podrzędny jednego **\<applicationSettings>** lub **\<userSettings>** .</span><span class="sxs-lookup"><span data-stu-id="a7eba-113">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| **\<value>**               | <span data-ttu-id="a7eba-114">Definiuje wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a7eba-114">Defines a setting's value.</span></span> <span data-ttu-id="a7eba-115">Element podrzędny **\<setting>** .</span><span class="sxs-lookup"><span data-stu-id="a7eba-115">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="a7eba-116">\<applicationSettings>, element</span><span class="sxs-lookup"><span data-stu-id="a7eba-116">\<applicationSettings> element</span></span>

<span data-ttu-id="a7eba-117">Ten element zawiera wszystkie **\<setting>** Tagi, które są specyficzne dla wystąpienia aplikacji na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="a7eba-117">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="a7eba-118">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a7eba-118">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="a7eba-119">\<userSettings>, element</span><span class="sxs-lookup"><span data-stu-id="a7eba-119">\<userSettings> element</span></span>

<span data-ttu-id="a7eba-120">Ten element zawiera wszystkie **\<setting>** Tagi, które są specyficzne dla użytkownika, który aktualnie używa aplikacji.</span><span class="sxs-lookup"><span data-stu-id="a7eba-120">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="a7eba-121">Nie definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="a7eba-121">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="a7eba-122">\<setting>, element</span><span class="sxs-lookup"><span data-stu-id="a7eba-122">\<setting> element</span></span>

<span data-ttu-id="a7eba-123">Ten element definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="a7eba-123">This element defines a setting.</span></span> <span data-ttu-id="a7eba-124">Ma następujące atrybuty.</span><span class="sxs-lookup"><span data-stu-id="a7eba-124">It has the following attributes.</span></span>

| <span data-ttu-id="a7eba-125">Atrybut</span><span class="sxs-lookup"><span data-stu-id="a7eba-125">Attribute</span></span>        | <span data-ttu-id="a7eba-126">Opis</span><span class="sxs-lookup"><span data-stu-id="a7eba-126">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="a7eba-127">**Nazwij**</span><span class="sxs-lookup"><span data-stu-id="a7eba-127">**name**</span></span>         | <span data-ttu-id="a7eba-128">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a7eba-128">Required.</span></span> <span data-ttu-id="a7eba-129">Unikatowy identyfikator ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a7eba-129">The unique ID of the setting.</span></span> <span data-ttu-id="a7eba-130">Ustawienia utworzone za pomocą programu Visual Studio są zapisywane z nazwą `ProjectName.Properties.Settings` .</span><span class="sxs-lookup"><span data-stu-id="a7eba-130">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="a7eba-131">**serializeAs**</span><span class="sxs-lookup"><span data-stu-id="a7eba-131">**serializeAs**</span></span> | <span data-ttu-id="a7eba-132">Wymagany.</span><span class="sxs-lookup"><span data-stu-id="a7eba-132">Required.</span></span> <span data-ttu-id="a7eba-133">Format służący do serializowania wartości do tekstu.</span><span class="sxs-lookup"><span data-stu-id="a7eba-133">The format to use for serializing the value to text.</span></span> <span data-ttu-id="a7eba-134">Prawidłowe wartości:</span><span class="sxs-lookup"><span data-stu-id="a7eba-134">Valid values are:</span></span><br><br><span data-ttu-id="a7eba-135">- `string`.</span><span class="sxs-lookup"><span data-stu-id="a7eba-135">- `string`.</span></span> <span data-ttu-id="a7eba-136">Wartość jest serializowana jako ciąg za pomocą <xref:System.ComponentModel.TypeConverter> .</span><span class="sxs-lookup"><span data-stu-id="a7eba-136">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="a7eba-137">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="a7eba-137">- `xml`.</span></span> <span data-ttu-id="a7eba-138">Wartość jest serializowana przy użyciu serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="a7eba-138">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="a7eba-139">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="a7eba-139">- `binary`.</span></span> <span data-ttu-id="a7eba-140">Wartość jest serializowana jako plik binarny kodowany tekstem przy użyciu serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="a7eba-140">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="a7eba-141">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="a7eba-141">- `custom`.</span></span> <span data-ttu-id="a7eba-142">Dostawca ustawień ma nieodłączną wiedzę o tym ustawieniu i serializować i deserializacji.</span><span class="sxs-lookup"><span data-stu-id="a7eba-142">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="a7eba-143">\<value>, element</span><span class="sxs-lookup"><span data-stu-id="a7eba-143">\<value> element</span></span>

<span data-ttu-id="a7eba-144">Ten element zawiera wartość ustawienia.</span><span class="sxs-lookup"><span data-stu-id="a7eba-144">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="a7eba-145">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7eba-145">Example</span></span>

<span data-ttu-id="a7eba-146">W poniższym przykładzie przedstawiono plik ustawień aplikacji, który definiuje dwa ustawienia dotyczące zakresu aplikacji i dwa ustawienia o zakresie użytkownika:</span><span class="sxs-lookup"><span data-stu-id="a7eba-146">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="a7eba-147">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7eba-147">See also</span></span>

- [<span data-ttu-id="a7eba-148">Przegląd ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7eba-148">Application Settings Overview</span></span>](../../winforms/advanced/application-settings-overview.md)
- [<span data-ttu-id="a7eba-149">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="a7eba-149">Application Settings Architecture</span></span>](../../winforms/advanced/application-settings-architecture.md)
