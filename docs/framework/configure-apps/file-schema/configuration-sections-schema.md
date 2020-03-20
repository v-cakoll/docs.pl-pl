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
ms.openlocfilehash: 28f936e6fd7c9e7f6f895396df8e8b8d36ab9139
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155326"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="59a59-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="59a59-102">Configuration sections schema</span></span>

<span data-ttu-id="59a59-103">Schemat sekcji konfiguracji zawiera elementy definiujące ustawienia niestandardowe w plikach konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="59a59-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="59a59-104">Aby uzyskać ogólne informacje na temat plików konfiguracyjnych i schematów, zobacz [Schemat pliku konfiguracji programu .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="59a59-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

<span data-ttu-id="59a59-105">[**\<konfiguracja>** ](configuration-element.md) 
 [\*\* \<konfiguracje>\*\*](configsections-element-for-configuration.md) 
 [\*\* \<wyczyść>\*\*](clear-element-for-configsections.md) 
 [\*\* \<usunąć \*\*](remove-element-for-configsections.md) 
 [\*\* \<sekcję \*\*](section-element.md)>>
 [\*\* \<sekcjiGrupa>\*\*](sectiongroup-element-for-configsections.md)</span><span class="sxs-lookup"><span data-stu-id="59a59-105">[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<clear>**](clear-element-for-configsections.md)
[**\<remove>**](remove-element-for-configsections.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)</span></span>

|     | <span data-ttu-id="59a59-106">Opis</span><span class="sxs-lookup"><span data-stu-id="59a59-106">Description</span></span> |
| --- | ----------- |
| [<span data-ttu-id="59a59-107">\*\* \<>\*\* \*\* \<konfisek>\*\*</span><span class="sxs-lookup"><span data-stu-id="59a59-107">**\<clear>** for **\<configSections>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="59a59-108">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="59a59-108">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="59a59-109">**\<wyraźne>**</span><span class="sxs-lookup"><span data-stu-id="59a59-109">**\<clear>**</span></span>](clear-element-for-configsections.md) | <span data-ttu-id="59a59-110">Czyści wszystkie wcześniej zdefiniowane sekcje i grupy sekcji.</span><span class="sxs-lookup"><span data-stu-id="59a59-110">Clears all previously defined sections and section groups.</span></span> |
| [<span data-ttu-id="59a59-111">**\<>konfiguracyjne**</span><span class="sxs-lookup"><span data-stu-id="59a59-111">**\<configSections>**</span></span>](configsections-element-for-configuration.md) | <span data-ttu-id="59a59-112">Zawiera sekcje konfiguracji i deklaracje obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="59a59-112">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="59a59-113">\*\* \<>\*\* usunięcia \*\* \<>konfisekcyjnych\*\*</span><span class="sxs-lookup"><span data-stu-id="59a59-113">**\<remove>** for **\<configSections>**</span></span>](remove-element-for-configsections.md) | <span data-ttu-id="59a59-114">Usuwa wstępnie zdefiniowaną sekcję lub grupę sekcji.</span><span class="sxs-lookup"><span data-stu-id="59a59-114">Removes a predefined section or section group.</span></span> |
| [<span data-ttu-id="59a59-115">>sekcji dla \*\* \<>konfisek\*\* i \*\* \<sekcjiGrupa>\*\* \*\* \<\*\*</span><span class="sxs-lookup"><span data-stu-id="59a59-115">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="59a59-116">Zawiera deklarację sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59a59-116">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="59a59-117">sectionGrupa>dla \*\* \<\*\* \*\* \<konfisek>\*\*</span><span class="sxs-lookup"><span data-stu-id="59a59-117">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="59a59-118">Definiuje obszar nazw dla sekcji konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="59a59-118">Defines a namespace for configuration sections.</span></span> |
