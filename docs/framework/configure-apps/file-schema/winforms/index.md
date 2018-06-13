---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18d8e1e24af73c9521b3a5bb45f1c86fc52ff1e9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755555"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="88c77-102">Sekcja konfiguracji programu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="88c77-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="88c77-103">Ustawienia konfiguracji formularzy systemu Windows umożliwiają aplikacji formularzy systemu Windows, do przechowywania i pobierania informacji o aplikacji dostosowane ustawienia, takie jak obsługi wielu monitorów, wysokiej rozdzielczości DPI pomocy technicznej i inne wstępnie zdefiniowane ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88c77-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="88c77-104">Ustawienia konfiguracji aplikacji formularzy systemu Windows są przechowywane w pliku konfiguracyjnym aplikacji `System.Windows.Forms.ApplicationConfigurationSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="88c77-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="88c77-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="88c77-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88c77-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="88c77-106">Attributes and elements</span></span>

<span data-ttu-id="88c77-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="88c77-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="88c77-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="88c77-108">Attributes</span></span>

<span data-ttu-id="88c77-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="88c77-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88c77-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="88c77-110">Child elements</span></span>

<span data-ttu-id="88c77-111">Element</span><span class="sxs-lookup"><span data-stu-id="88c77-111">Element</span></span>  |<span data-ttu-id="88c77-112">Opis</span><span class="sxs-lookup"><span data-stu-id="88c77-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="88c77-113">Dodaje klucz Ustawienia konfiguracji z określoną wartością</span><span class="sxs-lookup"><span data-stu-id="88c77-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="88c77-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="88c77-114">Parent elements</span></span>

<span data-ttu-id="88c77-115">Element</span><span class="sxs-lookup"><span data-stu-id="88c77-115">Element</span></span>  |<span data-ttu-id="88c77-116">Opis</span><span class="sxs-lookup"><span data-stu-id="88c77-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="88c77-117">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="88c77-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="88c77-118">Element główny w każdym pliku konfiguracyjnym używane przez środowisko uruchomieniowe języka wspólnego i formularze systemu Windows, aplikacje</span><span class="sxs-lookup"><span data-stu-id="88c77-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="88c77-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88c77-119">Remarks</span></span>

<span data-ttu-id="88c77-120">W programie .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element pozwala na skonfigurowanie aplikacji formularzy systemu Windows, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="88c77-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="88c77-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Elementu mogą zawierać jeden lub więcej podrzędnych [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elementów, z których każdy definiuje ustawienie określonej konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="88c77-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="88c77-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="88c77-122">See also</span></span>

<span data-ttu-id="88c77-123">[Schemat pliku konfiguracji](../index.md) </span><span class="sxs-lookup"><span data-stu-id="88c77-123">[Configuration File Schema](../index.md) </span></span>  
[<span data-ttu-id="88c77-124">Obsługa wysokiej rozdzielczości w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="88c77-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
