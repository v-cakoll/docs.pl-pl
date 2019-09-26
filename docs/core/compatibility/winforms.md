---
title: Windows Forms istotne zmiany — .NET Core
description: Wyświetla listę istotnych zmian w Windows Forms dla platformy .NET Core.
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 436088836ff5441e426379bb41f96821cbc7e500
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71272722"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="98013-103">Istotne zmiany w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="98013-103">Breaking changes in Windows Forms</span></span>

> [!IMPORTANT]
> <span data-ttu-id="98013-104">Ten artykuł jest w fazie tworzenia.</span><span class="sxs-lookup"><span data-stu-id="98013-104">This article is under construction.</span></span> <span data-ttu-id="98013-105">Nie jest to kompletna lista podstawowych zmian w programie .NET Core.</span><span class="sxs-lookup"><span data-stu-id="98013-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="98013-106">Aby uzyskać więcej informacji na temat podstawowych zmian w programie .NET Core, możesz zapoznać się [ze wszystkimi problemami dotyczącymi zmiany](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) w repozytorium dotnet/docs w witrynie GitHub.</span><span class="sxs-lookup"><span data-stu-id="98013-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span>

<span data-ttu-id="98013-107">Poniżej znajduje się lista istotnych zmian w Windows Forms według wersji platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="98013-107">The following is a list of breaking changes in Windows Forms by .NET Core version.</span></span>

## <a name="net-core-30-preview-9"></a><span data-ttu-id="98013-108">.NET Core 3,0 (wersja zapoznawcza 9)</span><span class="sxs-lookup"><span data-stu-id="98013-108">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Switch.System.Windows.Forms.AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[Switch.System.Windows.Forms.UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/deprecate-uselegacyimages.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/remove-serializationattribute.md)]

## <a name="net-core-30"></a><span data-ttu-id="98013-109">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="98013-109">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9pt](~/includes/core-changes/windowsforms/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/modernized-folderbrowserdialog.md)]
