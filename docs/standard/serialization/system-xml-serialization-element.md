---
title: <system.xml.serialization>, element
description: W tym artykule opisano element <system. XML. Serialization>, który jest elementem najwyższego poziomu służącego do kontrolowania serializacji XML.
ms.date: 03/30/2017
helpviewer_keywords:
- system.xml.serialization element
- XML serialization, configuration
- <system.xml.serialization> element
ms.assetid: 3ce45919-388a-418c-8968-6df0372c73ec
ms.openlocfilehash: 1e66220004d561f937d03c506e6f30db4ccc635b
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83380113"
---
# <a name="systemxmlserialization-element"></a><span data-ttu-id="697c6-103">\<Element> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="697c6-103">\<system.xml.serialization> Element</span></span>

<span data-ttu-id="697c6-104">Element najwyższego poziomu do sterowania serializacji XML.</span><span class="sxs-lookup"><span data-stu-id="697c6-104">The top-level element for controlling XML serialization.</span></span> <span data-ttu-id="697c6-105">Aby uzyskać więcej informacji na temat plików konfiguracji, zobacz [Schemat pliku konfiguracji](../../../docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="697c6-105">For more information about configuration files, see [Configuration File Schema](../../../docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="697c6-106">\<> konfiguracji </span><span class="sxs-lookup"><span data-stu-id="697c6-106">\<configuration></span></span>\
<span data-ttu-id="697c6-107">\<> system. XML. Serialization</span><span class="sxs-lookup"><span data-stu-id="697c6-107">\<system.xml.serialization></span></span>

## <a name="syntax"></a><span data-ttu-id="697c6-108">Składnia</span><span class="sxs-lookup"><span data-stu-id="697c6-108">Syntax</span></span>

```xml
<system.xml.serialization>
</system.xml.serialization>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="697c6-109">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="697c6-109">Attributes and Elements</span></span>

<span data-ttu-id="697c6-110">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="697c6-110">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="697c6-111">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="697c6-111">Attributes</span></span>

<span data-ttu-id="697c6-112">Brak.</span><span class="sxs-lookup"><span data-stu-id="697c6-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="697c6-113">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="697c6-113">Child Elements</span></span>

|<span data-ttu-id="697c6-114">Element</span><span class="sxs-lookup"><span data-stu-id="697c6-114">Element</span></span>|<span data-ttu-id="697c6-115">Opis</span><span class="sxs-lookup"><span data-stu-id="697c6-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="697c6-116">\<dateTimeSerialization, element></span><span class="sxs-lookup"><span data-stu-id="697c6-116">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)|<span data-ttu-id="697c6-117">Określa tryb serializacji <xref:System.DateTime> obiektów.</span><span class="sxs-lookup"><span data-stu-id="697c6-117">Determines the serialization mode of <xref:System.DateTime> objects.</span></span>|
|[<span data-ttu-id="697c6-118">\<schemaImporterExtensions, element></span><span class="sxs-lookup"><span data-stu-id="697c6-118">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)|<span data-ttu-id="697c6-119">Zawiera typy, które są używane przez <xref:System.Xml.Serialization.XmlSchemaImporter> dla mapowania typów XSD do typów programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="697c6-119">Contains types that are used by the <xref:System.Xml.Serialization.XmlSchemaImporter> for mapping of XSD types to .NET Framework types.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="697c6-120">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="697c6-120">Parent Elements</span></span>

|<span data-ttu-id="697c6-121">Element</span><span class="sxs-lookup"><span data-stu-id="697c6-121">Element</span></span>|<span data-ttu-id="697c6-122">Opis</span><span class="sxs-lookup"><span data-stu-id="697c6-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="697c6-123">\<> elementu konfiguracji</span><span class="sxs-lookup"><span data-stu-id="697c6-123">\<configuration> Element</span></span>](../../../docs/framework/configure-apps/file-schema/configuration-element.md)|<span data-ttu-id="697c6-124">Element główny w każdym pliku konfiguracji, który jest używany przez środowisko uruchomieniowe języka wspólnego i aplikacje .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="697c6-124">The root element in every configuration file that is used by the common language runtime and .NET Framework applications.</span></span>|

## <a name="example"></a><span data-ttu-id="697c6-125">Przykład</span><span class="sxs-lookup"><span data-stu-id="697c6-125">Example</span></span>

<span data-ttu-id="697c6-126">Poniższy przykład kodu ilustruje sposób określania trybu serializacji <xref:System.DateTime> obiektu i dodawania typów używanych przez <xref:System.Xml.Serialization.XmlSchemaImporter> podczas mapowania typów XSD na typy .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="697c6-126">The following code example illustrates how to specify the serialization mode of a <xref:System.DateTime> object, and the addition of types used by the <xref:System.Xml.Serialization.XmlSchemaImporter> when mapping XSD types to .NET Framework types.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="697c6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="697c6-127">See also</span></span>

- <xref:System.Xml.Serialization.XmlSchemaImporter>
- <xref:System.Xml.Serialization.Configuration.DateTimeSerializationSection.DateTimeSerializationMode>
- [<span data-ttu-id="697c6-128">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="697c6-128">Configuration File Schema</span></span>](../../../docs/framework/configure-apps/file-schema/index.md)
- [<span data-ttu-id="697c6-129">\<dateTimeSerialization, element></span><span class="sxs-lookup"><span data-stu-id="697c6-129">\<dateTimeSerialization> Element</span></span>](../../../docs/standard/serialization/datetimeserialization-element.md)
- [<span data-ttu-id="697c6-130">\<schemaImporterExtensions, element></span><span class="sxs-lookup"><span data-stu-id="697c6-130">\<schemaImporterExtensions> Element</span></span>](../../../docs/standard/serialization/schemaimporterextensions-element.md)
- [<span data-ttu-id="697c6-131">\<Dodaj element> dla \< schemaImporterExtensions></span><span class="sxs-lookup"><span data-stu-id="697c6-131">\<add> Element for \<schemaImporterExtensions></span></span>](../../../docs/standard/serialization/add-element-for-schemaimporterextensions.md)
