---
title: Sekcja konfiguracji formularzy systemu Windows
ms.custom: 
ms.date: 04/07/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b83f00f82de727812c5737915a6dc35ec98e4734
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="e926f-102">Sekcja konfiguracji formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e926f-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="e926f-103">Ustawienia konfiguracji formularzy systemu Windows umożliwiają aplikacji formularzy systemu Windows, do przechowywania i pobierania informacji o aplikacji dostosowane ustawienia, takie jak obsługi wielu monitorów, wysokiej rozdzielczości DPI pomocy technicznej i inne wstępnie zdefiniowane ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e926f-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="e926f-104">Ustawienia konfiguracji aplikacji formularzy systemu Windows są przechowywane w pliku konfiguracyjnym aplikacji `System.Windows.Forms.ApplicationConfigurationSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="e926f-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="e926f-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="e926f-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e926f-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="e926f-106">Attributes and elements</span></span>

<span data-ttu-id="e926f-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="e926f-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="e926f-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e926f-108">Attributes</span></span>

<span data-ttu-id="e926f-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="e926f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e926f-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="e926f-110">Child elements</span></span>

<span data-ttu-id="e926f-111">Element</span><span class="sxs-lookup"><span data-stu-id="e926f-111">Element</span></span>  |<span data-ttu-id="e926f-112">Opis</span><span class="sxs-lookup"><span data-stu-id="e926f-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="e926f-113">Dodaje klucz Ustawienia konfiguracji z określoną wartością</span><span class="sxs-lookup"><span data-stu-id="e926f-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="e926f-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="e926f-114">Parent elements</span></span>

<span data-ttu-id="e926f-115">Element</span><span class="sxs-lookup"><span data-stu-id="e926f-115">Element</span></span>  |<span data-ttu-id="e926f-116">Opis</span><span class="sxs-lookup"><span data-stu-id="e926f-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="e926f-117">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="e926f-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="e926f-118">Element główny w każdym pliku konfiguracyjnym używane przez środowisko uruchomieniowe języka wspólnego i formularze systemu Windows, aplikacje</span><span class="sxs-lookup"><span data-stu-id="e926f-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="e926f-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="e926f-119">Remarks</span></span>

<span data-ttu-id="e926f-120">W programie .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala na skonfigurowanie aplikacji formularzy systemu Windows, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e926f-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="e926f-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Elementu mogą zawierać jeden lub więcej podrzędnych [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elementów, z których każdy definiuje ustawienie określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="e926f-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="e926f-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e926f-122">See also</span></span>

<span data-ttu-id="e926f-123">[Schemat pliku konfiguracji](../index.md) </span><span class="sxs-lookup"><span data-stu-id="e926f-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="e926f-124">Obsługa wysokiej rozdzielczości w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e926f-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
