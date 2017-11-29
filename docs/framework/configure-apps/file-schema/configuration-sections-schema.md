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
ms.openlocfilehash: c668cf3d2f2c0bcffda185cea01edfb9e55c6d6c
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="b4d5d-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="b4d5d-102">Configuration sections schema</span></span>

<span data-ttu-id="b4d5d-103">Schemat sekcji konfiguracji zawiera elementy, które definiują ustawienia niestandardowe w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="b4d5d-104">Ogólne informacje na temat plików konfiguracji i schematów, zobacz [schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="b4d5d-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="b4d5d-105">[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="b4d5d-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="b4d5d-106">[**\<configSections >**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="b4d5d-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="b4d5d-107">[**\<Wyczyść >**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="b4d5d-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="b4d5d-108">[**\<Usuń >**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="b4d5d-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="b4d5d-109">[**\<sekcja >**](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="b4d5d-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="b4d5d-110">**\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="b4d5d-111">Opis</span><span class="sxs-lookup"><span data-stu-id="b4d5d-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="b4d5d-112">**\<Wyczyść >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="b4d5d-113">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="b4d5d-114">**\<Wyczyść >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="b4d5d-115">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="b4d5d-116">**\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="b4d5d-117">Zawiera konfigurację deklaracji sekcji i przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="b4d5d-118">**\<Usuń >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="b4d5d-119">Usuwa wstępnie zdefiniowanych sekcji lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="b4d5d-120">**\<sekcja >** dla  **\<configSections >** i  **\<sectionGroup >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="b4d5d-121">Zawiera deklaracji sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="b4d5d-122">**\<sectionGroup >** dla  **\<configSections >**</span><span class="sxs-lookup"><span data-stu-id="b4d5d-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="b4d5d-123">Definiuje obszar nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="b4d5d-123">Defines a namespace for configuration sections.</span></span> |
