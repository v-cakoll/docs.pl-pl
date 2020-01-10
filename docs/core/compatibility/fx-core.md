---
title: Istotne zmiany — .NET Framework do platformy .NET Core
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: e01ca522b7ec29e2f6db8a5a0c2fcdfc30a38168
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740901"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="ddacb-103">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddacb-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="ddacb-104">W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="ddacb-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="ddacb-105">Ponadto [technologie .NET Framework niedostępne w artykule .NET Core](../porting/net-framework-tech-unavailable.md) zawierają informacje o technologiach, które nie są obsługiwane przez platformę .NET Core, na przykład domeny aplikacji i komunikacja zdalna platformy .NET.</span><span class="sxs-lookup"><span data-stu-id="ddacb-105">In addition, the [.NET Framework technologies unavailable on .NET Core](../porting/net-framework-tech-unavailable.md) article provides information about technologies that aren't supported on .NET Core, for example, application domains and .NET remoting.</span></span>

<span data-ttu-id="ddacb-106">Istotne zmiany są pogrupowane według kategorii.</span><span class="sxs-lookup"><span data-stu-id="ddacb-106">Breaking changes are grouped by category.</span></span>

> [!NOTE]
> <span data-ttu-id="ddacb-107">Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ddacb-107">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="ddacb-108">Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.</span><span class="sxs-lookup"><span data-stu-id="ddacb-108">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="ddacb-109">CoreFx</span><span class="sxs-lookup"><span data-stu-id="ddacb-109">CoreFx</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a><span data-ttu-id="ddacb-110">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ddacb-110">Windows Forms</span></span>

<span data-ttu-id="ddacb-111">Aby uzyskać informacje o istotnych zmianach podczas migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core 3,0 lub nowszej, zobacz artykuł dotyczący [zmiany w Windows Forms (.NET Framework do platformy .NET Core)](../porting/winforms-breaking-changes.md).</span><span class="sxs-lookup"><span data-stu-id="ddacb-111">For information about breaking changes when you migrate a Windows Forms app from .NET Framework to .NET Core 3.0 or later, see [Breaking changes in Windows Forms (.NET Framework to .NET Core)](../porting/winforms-breaking-changes.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ddacb-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ddacb-112">See also</span></span>

- [<span data-ttu-id="ddacb-113">Technologie .NET Framework niedostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddacb-113">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
