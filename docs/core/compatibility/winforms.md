---
title: Windows Forms istotne zmiany — .NET Core
description: Wyświetla listę istotnych zmian w Windows Forms dla platformy .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 44bcde60f9e08d2e06a69c55e4ebe904bf5c449b
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116456"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="51800-103">Istotne zmiany w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51800-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="51800-104">Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="51800-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="51800-105">W tym artykule wymieniono istotne zmiany Windows Forms przez wersję programu .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="51800-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="51800-106">W przypadku uaktualniania aplikacji Windows Forms z .NET Framework lub poprzedniej wersji platformy .NET Core (3,0 lub nowszej) ten artykuł dotyczy Ciebie.</span><span class="sxs-lookup"><span data-stu-id="51800-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="51800-107">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="51800-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="51800-108">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="51800-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="51800-109">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="51800-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="51800-110">Formant. DefaultFont został zmieniony na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="51800-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="51800-111">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="51800-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="51800-112">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51800-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="51800-113">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="51800-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-114">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="51800-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-115">Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="51800-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-116">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="51800-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-117">Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="51800-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-118">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="51800-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-119">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="51800-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-120">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="51800-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="51800-121">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="51800-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="51800-122">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51800-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="51800-123">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="51800-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="51800-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="51800-124">.NET Core 3.0</span></span>

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

***

## <a name="see-also"></a><span data-ttu-id="51800-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51800-125">See also</span></span>

- [<span data-ttu-id="51800-126">Port aplikacji Windows Forms do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="51800-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
