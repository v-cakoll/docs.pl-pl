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
manager: markl
ms.openlocfilehash: 7af6342e9c05fc4e6c1bf4daac59db14ccdf22c7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32741740"
---
# <a name="application-settings-schema"></a><span data-ttu-id="1bb26-102">Schemat ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="1bb26-102">Application Settings schema</span></span>

<span data-ttu-id="1bb26-103">Ustawienia aplikacji pozwalają na przechowywanie i pobieranie ustawień zakresu aplikacji i zakresu użytkownika aplikacji formularzy systemu Windows lub programu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="1bb26-103">Application settings allow a Windows Forms or ASP.NET application to store and retrieve application-scoped and user-scoped settings.</span></span> <span data-ttu-id="1bb26-104">W tym kontekście *ustawienie* jest dowolne informacje, które mogą być specyficzne dla aplikacji lub specyficzne dla bieżącego użytkownika — wszystko z ciągu połączenia bazy danych dla użytkownika preferowana przez domyślny rozmiar okna.</span><span class="sxs-lookup"><span data-stu-id="1bb26-104">In this context, a *setting* is any piece of information that may be specific to the application or specific to the current user — anything from a database connection string to the user's preferred default window size.</span></span>

<span data-ttu-id="1bb26-105">Domyślnie ustawienia aplikacji w aplikacji formularzy systemu Windows używa <xref:System.Configuration.LocalFileSettingsProvider> klasy, która przechowuje ustawienia w pliku konfiguracji XML przy użyciu systemu konfiguracji platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="1bb26-105">By default, application settings in a Windows Forms application uses the <xref:System.Configuration.LocalFileSettingsProvider> class, which uses the .NET configuration system to store settings in an XML configuration file.</span></span> <span data-ttu-id="1bb26-106">Aby uzyskać więcej informacji na temat plików używanych przez ustawienia aplikacji, zobacz [Architektura ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span><span class="sxs-lookup"><span data-stu-id="1bb26-106">For more information about the files used by application settings, see [Application Settings Architecture](~/docs/framework/winforms/advanced/application-settings-architecture.md).</span></span>

<span data-ttu-id="1bb26-107">Ustawienia aplikacji definiuje następujące elementy jako część plików konfiguracyjnych, które są używane.</span><span class="sxs-lookup"><span data-stu-id="1bb26-107">Application settings defines the following elements as part of the configuration files it uses.</span></span>

| <span data-ttu-id="1bb26-108">Element</span><span class="sxs-lookup"><span data-stu-id="1bb26-108">Element</span></span>                    | <span data-ttu-id="1bb26-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1bb26-109">Description</span></span>                                                                           |
| -------------------------- | ------------------------------------------------------------------------------------- |
| <span data-ttu-id="1bb26-110">**\<applicationSettings >**</span><span class="sxs-lookup"><span data-stu-id="1bb26-110">**\<applicationSettings>**</span></span> | <span data-ttu-id="1bb26-111">Zawiera wszystkie  **\<Ustawienia >** tagi specyficzne dla aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bb26-111">Contains all **\<setting>** tags specific to the application.</span></span>                         |
| <span data-ttu-id="1bb26-112">**\<Ustawienia użytkownika >**</span><span class="sxs-lookup"><span data-stu-id="1bb26-112">**\<userSettings>**</span></span>        | <span data-ttu-id="1bb26-113">Zawiera wszystkie  **\<Ustawienia >** tagi specyficzne dla bieżącego użytkownika.</span><span class="sxs-lookup"><span data-stu-id="1bb26-113">Contains all **\<setting>** tags specific to the current user.</span></span>                        |
| <span data-ttu-id="1bb26-114">**\<Ustawienia >**</span><span class="sxs-lookup"><span data-stu-id="1bb26-114">**\<setting>**</span></span>             | <span data-ttu-id="1bb26-115">Definiuje ustawienie.</span><span class="sxs-lookup"><span data-stu-id="1bb26-115">Defines a setting.</span></span> <span data-ttu-id="1bb26-116">Jeden element podrzędny  **\<applicationSettings >** lub  **\<ustawienia użytkownika >**.</span><span class="sxs-lookup"><span data-stu-id="1bb26-116">Child of either **\<applicationSettings>** or **\<userSettings>**.</span></span> |
| <span data-ttu-id="1bb26-117">**\<wartość >**</span><span class="sxs-lookup"><span data-stu-id="1bb26-117">**\<value>**</span></span>               | <span data-ttu-id="1bb26-118">Definiuje wartości ustawień.</span><span class="sxs-lookup"><span data-stu-id="1bb26-118">Defines a setting's value.</span></span> <span data-ttu-id="1bb26-119">Element podrzędny  **\<Ustawienia >**.</span><span class="sxs-lookup"><span data-stu-id="1bb26-119">Child of **\<setting>**.</span></span>                                   |

## <a name="applicationsettings-element"></a><span data-ttu-id="1bb26-120">\<applicationSettings > — element</span><span class="sxs-lookup"><span data-stu-id="1bb26-120">\<applicationSettings> element</span></span>

<span data-ttu-id="1bb26-121">Ten element zawiera wszystkie  **\<Ustawienia >** tagi, które są specyficzne dla wystąpienia aplikacji na komputerze klienckim.</span><span class="sxs-lookup"><span data-stu-id="1bb26-121">This element contains all **\<setting>** tags that are specific to an instance of the application on a client computer.</span></span> <span data-ttu-id="1bb26-122">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1bb26-122">It defines no attributes.</span></span>

## <a name="usersettings-element"></a><span data-ttu-id="1bb26-123">\<Ustawienia użytkownika > — element</span><span class="sxs-lookup"><span data-stu-id="1bb26-123">\<userSettings> element</span></span>

<span data-ttu-id="1bb26-124">Ten element zawiera wszystkie  **\<Ustawienia >** tagi, które są specyficzne dla użytkownika, który jest obecnie przy użyciu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1bb26-124">This element contains all **\<setting>** tags that are specific to the user who is currently using the application.</span></span> <span data-ttu-id="1bb26-125">Definiuje żadnych atrybutów.</span><span class="sxs-lookup"><span data-stu-id="1bb26-125">It defines no attributes.</span></span>

## <a name="setting-element"></a><span data-ttu-id="1bb26-126">\<Ustawienia > — element</span><span class="sxs-lookup"><span data-stu-id="1bb26-126">\<setting> element</span></span>

<span data-ttu-id="1bb26-127">Ten element definiuje ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1bb26-127">This element defines a setting.</span></span> <span data-ttu-id="1bb26-128">Ma ona następujące atrybuty.</span><span class="sxs-lookup"><span data-stu-id="1bb26-128">It has the following attributes.</span></span>

| <span data-ttu-id="1bb26-129">Atrybut</span><span class="sxs-lookup"><span data-stu-id="1bb26-129">Attribute</span></span>        | <span data-ttu-id="1bb26-130">Opis</span><span class="sxs-lookup"><span data-stu-id="1bb26-130">Description</span></span> |
| ---------------- | ----------- |
| <span data-ttu-id="1bb26-131">**Nazwa**</span><span class="sxs-lookup"><span data-stu-id="1bb26-131">**name**</span></span>         | <span data-ttu-id="1bb26-132">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bb26-132">Required.</span></span> <span data-ttu-id="1bb26-133">Unikatowy identyfikator ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1bb26-133">The unique ID of the setting.</span></span> <span data-ttu-id="1bb26-134">Ustawienia utworzone za pomocą programu Visual Studio są zapisywane o nazwie `ProjectName.Properties.Settings`.</span><span class="sxs-lookup"><span data-stu-id="1bb26-134">Settings created through Visual Studio are saved with the name `ProjectName.Properties.Settings`.</span></span> |
| <span data-ttu-id="1bb26-135">**serializedAs**</span><span class="sxs-lookup"><span data-stu-id="1bb26-135">**serializedAs**</span></span> | <span data-ttu-id="1bb26-136">Wymagana.</span><span class="sxs-lookup"><span data-stu-id="1bb26-136">Required.</span></span> <span data-ttu-id="1bb26-137">Format używany do serializacji wartości Text.</span><span class="sxs-lookup"><span data-stu-id="1bb26-137">The format to use for serializing the value to text.</span></span> <span data-ttu-id="1bb26-138">Prawidłowe wartości to:</span><span class="sxs-lookup"><span data-stu-id="1bb26-138">Valid values are:</span></span><br><br><span data-ttu-id="1bb26-139">- `string`.</span><span class="sxs-lookup"><span data-stu-id="1bb26-139">- `string`.</span></span> <span data-ttu-id="1bb26-140">Wartość jest szeregowana jako parametry za pomocą <xref:System.ComponentModel.TypeConverter>.</span><span class="sxs-lookup"><span data-stu-id="1bb26-140">The value is serialized as a string using a <xref:System.ComponentModel.TypeConverter>.</span></span><br><span data-ttu-id="1bb26-141">- `xml`.</span><span class="sxs-lookup"><span data-stu-id="1bb26-141">- `xml`.</span></span> <span data-ttu-id="1bb26-142">Wartość jest serializowany za pomocą serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="1bb26-142">The value is serialized using XML serialization.</span></span><br><span data-ttu-id="1bb26-143">- `binary`.</span><span class="sxs-lookup"><span data-stu-id="1bb26-143">- `binary`.</span></span> <span data-ttu-id="1bb26-144">Wartość jest serializowany jako wartość binarną kodowany w formacie tekstowym za pomocą serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="1bb26-144">The value is serialized as text-encoded binary using binary serialization.</span></span><br /><span data-ttu-id="1bb26-145">- `custom`.</span><span class="sxs-lookup"><span data-stu-id="1bb26-145">- `custom`.</span></span> <span data-ttu-id="1bb26-146">Dostawca ustawień ma nieodłącznej wiedzy o to ustawienie i serializuje i zwalnia wykonuje serializację.</span><span class="sxs-lookup"><span data-stu-id="1bb26-146">The settings provider has inherent knowledge of this setting and serializes and de-serializes it.</span></span> |

## <a name="value-element"></a><span data-ttu-id="1bb26-147">\<wartość > — element</span><span class="sxs-lookup"><span data-stu-id="1bb26-147">\<value> element</span></span>

<span data-ttu-id="1bb26-148">Ten element zawiera wartości ustawienia.</span><span class="sxs-lookup"><span data-stu-id="1bb26-148">This element contains the value of a setting.</span></span>

## <a name="example"></a><span data-ttu-id="1bb26-149">Przykład</span><span class="sxs-lookup"><span data-stu-id="1bb26-149">Example</span></span>

<span data-ttu-id="1bb26-150">W poniższym przykładzie przedstawiono plik ustawień aplikacji, który definiuje dwa ustawienia zakresu aplikacji i dwa ustawienia zakresu użytkownika:</span><span class="sxs-lookup"><span data-stu-id="1bb26-150">The following example shows an application settings file that defines two application-scoped settings and two user-scoped settings:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1bb26-151">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bb26-151">See also</span></span>

<span data-ttu-id="1bb26-152">[Przegląd ustawień aplikacji](~/docs/framework/winforms/advanced/application-settings-overview.md) </span><span class="sxs-lookup"><span data-stu-id="1bb26-152">[Application Settings Overview](~/docs/framework/winforms/advanced/application-settings-overview.md) </span></span>  
[<span data-ttu-id="1bb26-153">Architektura ustawień aplikacji</span><span class="sxs-lookup"><span data-stu-id="1bb26-153">Application Settings Architecture</span></span>](~/docs/framework/winforms/advanced/application-settings-architecture.md)
