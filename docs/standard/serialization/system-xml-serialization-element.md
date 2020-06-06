---
title: <system.xml.serialization>, element
description: W tym artykule opisano element < System. XML. Serialization >, który jest elementem najwyższego poziomu służącego do kontrolowania serializacji XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: f69e80592e9321de64421b977a63b83d8be2ad9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289489"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="07d8c-103">\<system.xml.serialization> Element</span><span class="sxs-lookup"><span data-stu-id="07d8c-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="07d8c-104">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="07d8c-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="07d8c-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="07d8c-105">For more information about configuration files, see [Configuration File Schema](../../framework/configure-apps/file-schema/index.md).</span></span>

\<configuration>\
\<system.xml.serialization>

## <a name="syntax"></a><span data-ttu-id="07d8c-106">Składnia</span><span class="sxs-lookup"><span data-stu-id="07d8c-106">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="07d8c-107">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="07d8c-107">Attributes and Elements</span></span>

<span data-ttu-id="07d8c-108">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="07d8c-108">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="07d8c-109">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="07d8c-109">Attributes</span></span>

<span data-ttu-id="07d8c-110">Brak.</span><span class="sxs-lookup"><span data-stu-id="07d8c-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="07d8c-111">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="07d8c-111">Child Elements</span></span>

|<span data-ttu-id="07d8c-112">Element</span><span class="sxs-lookup"><span data-stu-id="07d8c-112">Element</span></span>|<span data-ttu-id="07d8c-113">Opis</span><span class="sxs-lookup"><span data-stu-id="07d8c-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07d8c-114">\<dateTimeSerialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="07d8c-114">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)|<span data-ttu-id="07d8c-115">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="07d8c-115">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="07d8c-116">\<schemaImporterExtensions>Postaci</span><span class="sxs-lookup"><span data-stu-id="07d8c-116">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)|<span data-ttu-id="07d8c-117">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07d8c-117">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="07d8c-118">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="07d8c-118">Parent Elements</span></span>

|<span data-ttu-id="07d8c-119">Element</span><span class="sxs-lookup"><span data-stu-id="07d8c-119">Element</span></span>|<span data-ttu-id="07d8c-120">Opis</span><span class="sxs-lookup"><span data-stu-id="07d8c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="07d8c-121">\<configuration>Postaci</span><span class="sxs-lookup"><span data-stu-id="07d8c-121">\<configuration> Element</span></span>](../../framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="07d8c-122">Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07d8c-122">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="07d8c-123">Przykład</span><span class="sxs-lookup"><span data-stu-id="07d8c-123">Example</span></span>

<span data-ttu-id="07d8c-124">Poniższy przykład kodu ilustruje sposób określania trybu serializacji <xref:System.DateTime> obiektu i dodawania typów używanych przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="07d8c-124">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

```xml
<system.xml.serialization>
    <xmlSerializer checkDeserializeAdvances="false" />
    <dateTimeSerialization mode = "Local" />
    <schemaImporterExtensions>
        <add
        name = "MobileCapabilities"
        type = "System.Web.Mobile.MobileCapabilities,
        System.Web.Mobile, Version=2.0.0.0, Culture=neutral,
        PublicKeyToken=b03f5f6f11d40a3a" />
    </schemaImporterExtensions>
</system.xml.serialization>
```

## <a name="see-also"></a><span data-ttu-id="07d8c-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07d8c-125">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="07d8c-126">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="07d8c-126">Configuration File Schema</span></span>](../../framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="07d8c-127">\<dateTimeSerialization>Postaci</span><span class="sxs-lookup"><span data-stu-id="07d8c-127">\<dateTimeSerialization> Element</span></span>](datetimeserialization-element.md)
- [<span data-ttu-id="07d8c-128">\<schemaImporterExtensions>Postaci</span><span class="sxs-lookup"><span data-stu-id="07d8c-128">\<schemaImporterExtensions> Element</span></span>](schemaimporterextensions-element.md)
- [<span data-ttu-id="07d8c-129">\<add>Element dla\<schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="07d8c-129">\<add> Element for \<schemaImporterExtensions></span></span>](add-element-for-schemaimporterextensions.md)
