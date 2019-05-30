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
ms.openlocfilehash: c7559a95099608ea462c838591ddb43e18d8f80c
ms.sourcegitcommit: 621a5f6df00152006160987395b93b5b55f7ffcd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2019
ms.locfileid: "66301236"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="6e7a4-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="6e7a4-102">Configuration sections schema</span></span>

<span data-ttu-id="6e7a4-103">Schemat sekcji konfiguracji zawiera elementy, które definiują ustawienia niestandardowe w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="6e7a4-104">Aby uzyskać ogólne informacje na temat plików konfiguracyjnych i schematów, zobacz [schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span><span class="sxs-lookup"><span data-stu-id="6e7a4-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](~/docs/framework/configure-apps/file-schema/index.md).</span></span>

<span data-ttu-id="6e7a4-105">[ **\<Konfiguracja >** ](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="6e7a4-105">[**\<configuration>**](~/docs/framework/configure-apps/file-schema/configuration-element.md) </span></span>  
<span data-ttu-id="6e7a4-106">[ **\<configSections>** ](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span><span class="sxs-lookup"><span data-stu-id="6e7a4-106">[**\<configSections>**](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) </span></span>  
<span data-ttu-id="6e7a4-107">[ **\<clear>** ](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="6e7a4-107">[**\<clear>**](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) </span></span>  
<span data-ttu-id="6e7a4-108">[ **\<remove>** ](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span><span class="sxs-lookup"><span data-stu-id="6e7a4-108">[**\<remove>**](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) </span></span>  
<span data-ttu-id="6e7a4-109">[ **\<sekcja >** ](~/docs/framework/configure-apps/file-schema/section-element.md) </span><span class="sxs-lookup"><span data-stu-id="6e7a4-109">[**\<section>**](~/docs/framework/configure-apps/file-schema/section-element.md) </span></span>  
[<span data-ttu-id="6e7a4-110"> *\*\<sectionGroup>** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-110">**\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="6e7a4-111">Opis</span><span class="sxs-lookup"><span data-stu-id="6e7a4-111">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="6e7a4-112"> *\*\<Wyczyść >** dla  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-112">**\<clear>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="6e7a4-113">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-113">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="6e7a4-114"> *\*\<clear>** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-114">**\<clear>**</span></span>](~/docs/framework/configure-apps/file-schema/clear-element-for-configsections.md) | <span data-ttu-id="6e7a4-115">Czyści wszystkie wcześniej zdefiniowanego sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-115">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="6e7a4-116"> *\*\<configSections>** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-116">**\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/configsections-element-for-configuration.md) | <span data-ttu-id="6e7a4-117">Zawiera deklaracje sekcji i przestrzeni nazw konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-117">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="6e7a4-118"> *\*\<Usuń >** dla  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-118">**\<remove>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/remove-element-for-configsections.md) | <span data-ttu-id="6e7a4-119">Usuwa sekcję wstępnie zdefiniowanych lub grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-119">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="6e7a4-120"> *\*\<sekcja >** dla  *\*\<configSections >** i  *\*\<sectionGroup >** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-120">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](~/docs/framework/configure-apps/file-schema/section-element.md) | <span data-ttu-id="6e7a4-121">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-121">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="6e7a4-122"> *\*\<sectionGroup >** dla  *\*\<configSections >** </span><span class="sxs-lookup"><span data-stu-id="6e7a4-122">**\<sectionGroup>** for **\<configSections>**</span></span>](~/docs/framework/configure-apps/file-schema/sectiongroup-element-for-configsections.md) | <span data-ttu-id="6e7a4-123">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="6e7a4-123">Defines a namespace for configuration sections.</span></span> |
