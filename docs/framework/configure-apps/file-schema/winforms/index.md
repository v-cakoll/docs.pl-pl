---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: bbb2c4157ba702182056c98c959a60569e8c3d1e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649481"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="d45bb-102">Sekcja konfiguracji programu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d45bb-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="d45bb-103">Ustawienia konfiguracji formularze Windows umożliwiają aplikacji Windows Forms, do przechowywania i pobierania informacji o aplikacji dostosowane ustawienia, takie jak obsługa wielu monitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d45bb-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="d45bb-104">Ustawienia konfiguracji aplikacji Windows Forms są przechowywane w pliku konfiguracyjnym aplikacji `System.Windows.Forms.ApplicationConfigurationSection` elementu.</span><span class="sxs-lookup"><span data-stu-id="d45bb-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="d45bb-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="d45bb-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d45bb-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="d45bb-106">Attributes and elements</span></span>

<span data-ttu-id="d45bb-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="d45bb-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d45bb-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="d45bb-108">Attributes</span></span>

<span data-ttu-id="d45bb-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="d45bb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d45bb-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="d45bb-110">Child elements</span></span>

<span data-ttu-id="d45bb-111">Element</span><span class="sxs-lookup"><span data-stu-id="d45bb-111">Element</span></span>  |<span data-ttu-id="d45bb-112">Opis</span><span class="sxs-lookup"><span data-stu-id="d45bb-112">Description</span></span> |
---------|---------|
[`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) | <span data-ttu-id="d45bb-113">Dodaje klucz Ustawienia konfiguracji z określoną wartością</span><span class="sxs-lookup"><span data-stu-id="d45bb-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="d45bb-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="d45bb-114">Parent elements</span></span>

<span data-ttu-id="d45bb-115">Element</span><span class="sxs-lookup"><span data-stu-id="d45bb-115">Element</span></span>  |<span data-ttu-id="d45bb-116">Opis</span><span class="sxs-lookup"><span data-stu-id="d45bb-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="d45bb-117">\<Konfiguracja ></span><span class="sxs-lookup"><span data-stu-id="d45bb-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="d45bb-118">Element główny w każdym pliku konfiguracji używane przez środowisko uruchomieniowe języka wspólnego i Windows Forms aplikacji</span><span class="sxs-lookup"><span data-stu-id="d45bb-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="d45bb-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d45bb-119">Remarks</span></span>

<span data-ttu-id="d45bb-120">Począwszy od .NET Framework 4.7 `<System.Windows.Forms.ApplicationConfigurationSection>` elementu umożliwia skonfigurowanie aplikacji Windows Forms, aby wykorzystać funkcje dodane w najnowszych wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="d45bb-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span> 

<span data-ttu-id="d45bb-121">`<System.Windows.Forms.ApplicationConfigurationSection>` Element może zawierać co najmniej jedną podrzędną [ `<add>` ](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elementów, z których każdy definiuje ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="d45bb-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](../../../../../docs/framework/configure-apps/file-schema/winforms/windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="d45bb-122">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d45bb-122">See also</span></span>

- [<span data-ttu-id="d45bb-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="d45bb-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="d45bb-124">Obsługa wysokiej rozdzielczości w formularzach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d45bb-124">High DPI Support in Windows Forms</span></span>](../../../../../docs/framework/winforms/high-dpi-support-in-windows-forms.md)
