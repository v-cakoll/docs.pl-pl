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
ms.openlocfilehash: fc43a9c32ba33629b6e89120cf57f6d212ab3a56
ms.sourcegitcommit: 2543a78be6e246aa010a01decf58889de53d1636
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/17/2020
ms.locfileid: "86441664"
---
# <a name="configuration-sections-schema"></a><span data-ttu-id="2ded1-102">Schemat sekcji konfiguracji</span><span class="sxs-lookup"><span data-stu-id="2ded1-102">Configuration sections schema</span></span>

<span data-ttu-id="2ded1-103">Schemat sekcji konfiguracji zawiera elementy, które definiują ustawienia niestandardowe w plikach konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="2ded1-103">The configuration sections schema contains elements that define custom settings in configuration files.</span></span> <span data-ttu-id="2ded1-104">Aby uzyskać ogólne informacje o plikach i schematach konfiguracji, zobacz [Schemat pliku konfiguracji dla .NET Framework](index.md).</span><span class="sxs-lookup"><span data-stu-id="2ded1-104">For general information on configuration files and schemas, see [Configuration file schema for the .NET Framework](index.md).</span></span>

[**\<configuration>**](configuration-element.md)
[**\<configSections>**](configsections-element-for-configuration.md)
[**\<section>**](section-element.md)
[**\<sectionGroup>**](sectiongroup-element-for-configsections.md)

|     | <span data-ttu-id="2ded1-105">Opis</span><span class="sxs-lookup"><span data-stu-id="2ded1-105">Description</span></span> |
| --- | ----------- |
| [**\<configSections>**](configsections-element-for-configuration.md) | <span data-ttu-id="2ded1-106">Zawiera sekcję konfiguracyjną i deklaracje przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2ded1-106">Contains configuration section and namespace declarations.</span></span> |
| [<span data-ttu-id="2ded1-107">**\<section>** dla **\<configSections>** i**\<sectionGroup>**</span><span class="sxs-lookup"><span data-stu-id="2ded1-107">**\<section>** for **\<configSections>** and **\<sectionGroup>**</span></span>](section-element.md) | <span data-ttu-id="2ded1-108">Zawiera deklarację sekcji konfiguracyjnej.</span><span class="sxs-lookup"><span data-stu-id="2ded1-108">Contains a configuration section declaration.</span></span> |
| [<span data-ttu-id="2ded1-109">**\<sectionGroup>** dla**\<configSections>**</span><span class="sxs-lookup"><span data-stu-id="2ded1-109">**\<sectionGroup>** for **\<configSections>**</span></span>](sectiongroup-element-for-configsections.md) | <span data-ttu-id="2ded1-110">Definiuje przestrzeń nazw dla sekcji konfiguracyjnych.</span><span class="sxs-lookup"><span data-stu-id="2ded1-110">Defines a namespace for configuration sections.</span></span> |

<a name="dep"></a>

## <a name="unimplemented-elements"></a><span data-ttu-id="2ded1-111">Niezaimplementowane elementy</span><span class="sxs-lookup"><span data-stu-id="2ded1-111">Unimplemented elements</span></span>

<span data-ttu-id="2ded1-112">Następujące elementy nie mają wpływu i nie powinny być używane:</span><span class="sxs-lookup"><span data-stu-id="2ded1-112">The following elements have no impact and should not be used:</span></span>

* **\<clear>**
* **\<remove>**
