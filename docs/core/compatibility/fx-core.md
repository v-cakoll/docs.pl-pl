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
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core

W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika. Ponadto [technologie .NET Framework niedostępne w artykule .NET Core](../porting/net-framework-tech-unavailable.md) zawierają informacje o technologiach, które nie są obsługiwane przez platformę .NET Core, na przykład domeny aplikacji i komunikacja zdalna platformy .NET.

Istotne zmiany są pogrupowane według kategorii.

> [!NOTE]
> Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core. Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.

## <a name="corefx"></a>CoreFx

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

## <a name="windows-forms"></a>Windows Forms

Aby uzyskać informacje o istotnych zmianach podczas migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core 3,0 lub nowszej, zobacz artykuł dotyczący [zmiany w Windows Forms (.NET Framework do platformy .NET Core)](../porting/winforms-breaking-changes.md).

## <a name="see-also"></a>Zobacz także

- [Technologie .NET Framework niedostępne w programie .NET Core](../porting/net-framework-tech-unavailable.md)
