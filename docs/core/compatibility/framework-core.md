---
title: Istotne zmiany, .NET Framework do programu .NET Core 3,0 — .NET Core
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core 3,0 dla Windows Forms i Windows Presentation Foundation.
ms.date: 09/10/2019
ms.openlocfilehash: a374e35192c7aad07e986e0e0b75039642744edc
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73089572"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core-30"></a>Istotne zmiany dotyczące migracji z .NET Framework do programu .NET Core 3,0

> [!IMPORTANT]
> Ten artykuł jest w fazie tworzenia. Nie jest to kompletna lista podstawowych zmian w programie .NET Core. Aby uzyskać więcej informacji na temat podstawowych zmian w programie .NET Core, możesz zapoznać się [ze wszystkimi problemami dotyczącymi zmiany](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) w repozytorium dotnet/docs w witrynie GitHub. 

W przypadku migrowania Windows Forms lub Windows Presentation Foundation aplikacji z .NET Framework do programu .NET Core 3,0 zapoznaj się z następującymi tematami dotyczącymi istotnych zmian, które mogą mieć wpływ na aplikację:

## <a name="windows-forms"></a>Windows Forms

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]
