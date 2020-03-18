---
title: Zmiany łamania formularzy systemu Windows
description: Wyświetla listę zmian w formularzach systemu Windows dla programu .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 7fba78382d011bc9d489924fa185a44e598c5a76
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399099"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="b4ae6-103">Krytyczne zmiany w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4ae6-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="b4ae6-104">Obsługa formularzy systemu Windows została dodana do programu .NET Core w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="b4ae6-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="b4ae6-105">W tym artykule wymieniono zmiany dotyczące łamania formularzy systemu Windows według wersji .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="b4ae6-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="b4ae6-106">Jeśli uaktualniasz aplikację Windows Forms z platformy .NET Framework lub z poprzedniej wersji programu .NET Core (3.0 lub nowszej), ten artykuł ma zastosowanie do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b4ae6-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="b4ae6-107">Na tej stronie udokumentowane są następujące zmiany dotyczące zasad:</span><span class="sxs-lookup"><span data-stu-id="b4ae6-107">The following breaking changes are documented on this page:</span></span>

- [<span data-ttu-id="b4ae6-108">Usunięte formanty</span><span class="sxs-lookup"><span data-stu-id="b4ae6-108">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="b4ae6-109">Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="b4ae6-109">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="b4ae6-110">Control.DefaultFont zmieniono na Segoe UI 9 pkt</span><span class="sxs-lookup"><span data-stu-id="b4ae6-110">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="b4ae6-111">Modernizacja folderuOkno przeglądarki</span><span class="sxs-lookup"><span data-stu-id="b4ae6-111">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="b4ae6-112">SerializableAttribute usunięte z niektórych typów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4ae6-112">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="b4ae6-113">Przełącznik zgodności AllowUpdateChildControlForTabControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-113">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-114">Przełącznik zgodności DomainUpDown.UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-114">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-115">Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-115">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-116">Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-116">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-117">Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-117">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-118">Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-118">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-119">UseLegacyContextMenuStripSourceControlValue przełącznik zgodności nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-119">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-120">Przełącznik zgodności UseLegacyImages nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b4ae6-120">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="b4ae6-121">Zmiana dostępu dla accessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="b4ae6-121">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="b4ae6-122">Zduplikowane interfejsy API usunięte z formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b4ae6-122">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a><span data-ttu-id="b4ae6-123">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="b4ae6-123">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b4ae6-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b4ae6-124">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b4ae6-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b4ae6-125">See also</span></span>

- [<span data-ttu-id="b4ae6-126">Przenoszenie aplikacji formularzy systemu Windows do usługi .NET Core</span><span class="sxs-lookup"><span data-stu-id="b4ae6-126">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
