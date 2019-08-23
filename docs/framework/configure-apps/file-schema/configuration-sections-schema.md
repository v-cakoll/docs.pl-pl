---
title: Schemat sekcji konfiguracji
ms.date: 05/02/2017
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: rpetrusha
ms.author: mairaw
ms.openlocfilehash: 120733873a7ea29303fe7f82c4c324d411532897
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921204"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="f3674-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="f3674-102">Configuration sections schema</span></span>

<span data-ttu-id="f3674-103">Schemat sekcji konfiguracji zawiera elementy, które definiują ustawienia niestandardowe w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="f3674-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="f3674-104">Aby uzyskać ogólne informacje o plikach i schematach konfiguracji, zobacz [Schemat pliku konfiguracji dla .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="f3674-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="f3674-105">[ **\<> konfiguracji**](configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f3674-105">[**\<configuration>**](configuration-element.md) </span></span>  
<span data-ttu-id="f3674-106">[ **\<configSections >** ](configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="f3674-106">[**\<configSections>**](configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="f3674-107">[ **\<clear>** ](clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="f3674-107">[**\<clear>**](clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="f3674-108">[ **\<remove>** ](remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="f3674-108">[**\<remove>**](remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="f3674-109">[ **\<sekcja >** ](section-element.md) </span><span class="sxs-lookup"><span data-stu-id="f3674-109">[**\<section>**](section-element.md) </span></span>  
[<span data-ttu-id="f3674-110"> **\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="f3674-110">**\<sectionGroup>**</span></span>](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="f3674-111">Opis</span><span class="sxs-lookup"><span data-stu-id="f3674-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="f3674-112">Wyczyść > dla  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="f3674-112">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="f3674-113">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="f3674-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="f3674-114"> **\<clear>** </span><span class="sxs-lookup"><span data-stu-id="f3674-114">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="f3674-115">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="f3674-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="f3674-116"> **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="f3674-116">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="f3674-117">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f3674-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="f3674-118">Usuń > dla  **\<**  **configSections>\<** </span><span class="sxs-lookup"><span data-stu-id="f3674-118">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="f3674-119">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="f3674-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="f3674-120">sekcja > **dla >configSectionsi\<** **> \<**  **\<** </span><span class="sxs-lookup"><span data-stu-id="f3674-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="f3674-121">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="f3674-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="f3674-122">> w sekcji elementu  **\<**  **\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="f3674-122">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="f3674-123">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f3674-123">Defines a namespace for configuration sections.</span></span> |
