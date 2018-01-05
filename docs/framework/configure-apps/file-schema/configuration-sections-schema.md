---
title: Schemat sekcji konfiguracji
ms.date: 05/02/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- configuration settings [.NET Framework], custom
- schema configuration settings
- configuration sections [.NET Framework]
- custom elements
- configuration schema [.NET Framework], custom settings in configuration files
- elements [.NET Framework], custom settings in configuration files
ms.assetid: 6e4cc793-c526-4007-b4e9-37d56295f2cb
author: guardrex
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: da9af8fd24f1bf6e6effd411ad37490a4ee08804
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="973e9-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="973e9-102">Configuration sections schema</span></span>

<span data-ttu-id="973e9-103">Schemat sekcji konfiguracji zawiera elementy, które definiują ustawienia niestandardowe w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="973e9-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="973e9-104">Ogólne informacje na temat plików konfiguracji i schematów, zobacz [schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="973e9-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="973e9-105">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="973e9-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="973e9-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="973e9-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="973e9-107">[**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="973e9-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="973e9-108">[**\<Usuń >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="973e9-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="973e9-109">[**\<sekcja >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="973e9-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="973e9-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="973e9-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="973e9-111">Opis</span><span class="sxs-lookup"><span data-stu-id="973e9-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="973e9-112">**\<Wyczyść >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="973e9-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="973e9-113">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="973e9-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="973e9-114">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="973e9-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="973e9-115">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="973e9-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="973e9-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="973e9-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="973e9-117">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="973e9-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="973e9-118">**\<Usuń >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="973e9-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="973e9-119">Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="973e9-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="973e9-120">**\<sekcja >** dla  **\<configSections >** i  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="973e9-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="973e9-121">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="973e9-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="973e9-122">**\<sectionGroup >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="973e9-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="973e9-123">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="973e9-123">Defines a namespace for configuration sections.</span></span> |
