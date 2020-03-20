---
title: Sekcja konfiguracji programu Windows Forms
ms.date: 04/07/2017
ms.assetid: 6eb142d5-fc98-40e2-9d90-84733f2a27ba
ms.openlocfilehash: 4de61ae3cb5eb8a3fc226881e2b7f842030dfddf
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151835"
---
# <a name="windows-forms-configuration-section"></a><span data-ttu-id="3343a-102">Sekcja konfiguracji programu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3343a-102">Windows Forms Configuration Section</span></span>
<span data-ttu-id="3343a-103">Ustawienia konfiguracji Formularzy systemu Windows umożliwiają aplikacji Windows Forms przechowywanie i pobieranie informacji o dostosowanych ustawieniach aplikacji, takich jak obsługa wielu monitorów, obsługa wysokiej rozdzielczości DPI i inne wstępnie zdefiniowane ustawienia konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3343a-103">Windows Forms configuration settings allow a Windows Forms app to store and retrieve information about customized application settings such as multi-monitor support, high DPI support, and other predefined configuration settings.</span></span>

<span data-ttu-id="3343a-104">Ustawienia konfiguracji aplikacji Windows Forms są przechowywane `System.Windows.Forms.ApplicationConfigurationSection` w elemencie pliku konfiguracji aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3343a-104">Windows Forms application configuration settings are stored in an application configuration file's `System.Windows.Forms.ApplicationConfigurationSection` element.</span></span>

## <a name="syntax"></a><span data-ttu-id="3343a-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="3343a-105">Syntax</span></span>

```xml
<configuration>
  <System.Windows.Forms.ApplicationConfigurationSection>
  ...
  </System.Windows.Forms.ApplicationConfigurationSection>
</configuration>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3343a-106">Atrybuty i elementy</span><span class="sxs-lookup"><span data-stu-id="3343a-106">Attributes and elements</span></span>

<span data-ttu-id="3343a-107">W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.</span><span class="sxs-lookup"><span data-stu-id="3343a-107">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="3343a-108">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="3343a-108">Attributes</span></span>

<span data-ttu-id="3343a-109">Brak.</span><span class="sxs-lookup"><span data-stu-id="3343a-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3343a-110">Elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="3343a-110">Child elements</span></span>

<span data-ttu-id="3343a-111">Element</span><span class="sxs-lookup"><span data-stu-id="3343a-111">Element</span></span>  |<span data-ttu-id="3343a-112">Opis</span><span class="sxs-lookup"><span data-stu-id="3343a-112">Description</span></span> |
---------|---------|
[`<add>`](windows-forms-add-configuration-element.md) | <span data-ttu-id="3343a-113">Dodaje klucz ustawień konfiguracji o określonej wartości</span><span class="sxs-lookup"><span data-stu-id="3343a-113">Adds a configuration setting key with a specified value</span></span> |

### <a name="parent-elements"></a><span data-ttu-id="3343a-114">Elementy nadrzędne</span><span class="sxs-lookup"><span data-stu-id="3343a-114">Parent elements</span></span>

<span data-ttu-id="3343a-115">Element</span><span class="sxs-lookup"><span data-stu-id="3343a-115">Element</span></span>  |<span data-ttu-id="3343a-116">Opis</span><span class="sxs-lookup"><span data-stu-id="3343a-116">Description</span></span> |
---------|---------|
[<span data-ttu-id="3343a-117">\<>konfiguracyjne</span><span class="sxs-lookup"><span data-stu-id="3343a-117">\<configuration></span></span>](../configuration-element.md) | <span data-ttu-id="3343a-118">Element główny w każdym pliku konfiguracyjnym używanym przez środowisko wykonawcze języka wspólnego i aplikacje Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3343a-118">The root element in every configuration file used by the common language runtime and Windows Forms applications</span></span> |

## <a name="remarks"></a><span data-ttu-id="3343a-119">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3343a-119">Remarks</span></span>

<span data-ttu-id="3343a-120">Począwszy od programu .NET Framework 4.7, `<System.Windows.Forms.ApplicationConfigurationSection>` element umożliwia skonfigurowanie aplikacji Windows Forms, aby korzystać z funkcji dodanych w ostatnich wersjach programu .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="3343a-120">Starting with the .NET Framework 4.7, the `<System.Windows.Forms.ApplicationConfigurationSection>` element allows you to configure Windows Forms applications to take advantage of features added in recent releases of the .NET Framework.</span></span>

<span data-ttu-id="3343a-121">Element `<System.Windows.Forms.ApplicationConfigurationSection>` może zawierać jeden [`<add>`](windows-forms-add-configuration-element.md) lub więcej elementów podrzędnych, z których każdy definiuje określone ustawienie konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="3343a-121">The `<System.Windows.Forms.ApplicationConfigurationSection>` element can include one or more child [`<add>`](windows-forms-add-configuration-element.md) elements, each of which defines a specific configuration setting.</span></span>

## <a name="see-also"></a><span data-ttu-id="3343a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3343a-122">See also</span></span>

- [<span data-ttu-id="3343a-123">Schemat pliku konfiguracji</span><span class="sxs-lookup"><span data-stu-id="3343a-123">Configuration File Schema</span></span>](../index.md)
- [<span data-ttu-id="3343a-124">Obsługa wysokiej rozdzielczości DPI w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3343a-124">High DPI Support in Windows Forms</span></span>](../../../winforms/high-dpi-support-in-windows-forms.md)
