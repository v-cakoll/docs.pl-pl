---
title: Istotne zmiany dla WinForms-.NET Framework do programu .NET Core
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core dla aplikacji Windows Forms.
ms.date: 11/27/2019
ms.openlocfilehash: cc1f319dcc83a633c81c49195d743784fe5916d9
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643978"
---
# <a name="breaking-changes-in-windows-forms-net-framework-to-net-core"></a><span data-ttu-id="0d706-103">Istotne zmiany w Windows Forms (.NET Framework do programu .NET Core)</span><span class="sxs-lookup"><span data-stu-id="0d706-103">Breaking changes in Windows Forms (.NET Framework to .NET Core)</span></span>

<span data-ttu-id="0d706-104">Obsługa WPF i Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="0d706-104">WPF and Windows Forms support were added to .NET Core in version 3.0.</span></span> <span data-ttu-id="0d706-105">W przypadku migrowania aplikacji Windows Forms lub Windows Presentation Foundation z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="0d706-105">If you're migrating a Windows Forms or Windows Presentation Foundation app from .NET Framework to .NET Core, the breaking changes listed in this article may affect your app.</span></span>

<span data-ttu-id="0d706-106">Istotne zmiany są pogrupowane według wersji platformy .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="0d706-106">Breaking changes are grouped by the .NET Core version in which they were introduced.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="0d706-107">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="0d706-107">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

## <a name="net-core-30"></a><span data-ttu-id="0d706-108">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="0d706-108">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

## <a name="see-also"></a><span data-ttu-id="0d706-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d706-109">See also</span></span>

- [<span data-ttu-id="0d706-110">Oszacowanie istotnych zmian w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="0d706-110">Evaluate breaking changes in .NET Core</span></span>](../compatibility/index.md)
- [<span data-ttu-id="0d706-111">Istotne zmiany w Windows Forms (.NET Core do .NET Core)</span><span class="sxs-lookup"><span data-stu-id="0d706-111">Breaking changes in Windows Forms (.NET Core to .NET Core)</span></span>](../compatibility/winforms.md)
