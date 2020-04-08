---
title: Formularze systemu Windows z podziałem na zmiany
description: Wyświetla listę przełomowych zmian w formularzach systemu Windows dla platformy .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 25c568a8a0092a9c4874419c64c7dcebea4dce9e
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888141"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="b8d3c-103">Łamanie zmian w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8d3c-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="b8d3c-104">Obsługa formularzy systemu Windows została dodana do platformy .NET Core w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="b8d3c-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="b8d3c-105">W tym artykule wymieniono przełomowe zmiany dla formularzy systemu Windows według wersji .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="b8d3c-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="b8d3c-106">Jeśli uaktualniasz aplikację Formularze systemu Windows z programu .NET Framework lub z poprzedniej wersji programu .NET Core (3.0 lub nowszej), ten artykuł ma zastosowanie do Ciebie.</span><span class="sxs-lookup"><span data-stu-id="b8d3c-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="b8d3c-107">Na tej stronie są udokumentowane następujące zmiany podziału:</span><span class="sxs-lookup"><span data-stu-id="b8d3c-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="b8d3c-108">Przełomowa zmiana</span><span class="sxs-lookup"><span data-stu-id="b8d3c-108">Breaking change</span></span> | <span data-ttu-id="b8d3c-109">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="b8d3c-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="b8d3c-110">Interfejsy API WinForms teraz rzucać ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="b8d3c-110">WinForms APIs now throw ArgumentNullException</span></span>](#winforms-apis-now-throw-argumentnullexception) | <span data-ttu-id="b8d3c-111">5.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-111">5.0</span></span> |
| [<span data-ttu-id="b8d3c-112">Usunięto kontrolki</span><span class="sxs-lookup"><span data-stu-id="b8d3c-112">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="b8d3c-113">3.1</span><span class="sxs-lookup"><span data-stu-id="b8d3c-113">3.1</span></span> |
| [<span data-ttu-id="b8d3c-114">Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="b8d3c-114">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="b8d3c-115">3.1</span><span class="sxs-lookup"><span data-stu-id="b8d3c-115">3.1</span></span> |
| [<span data-ttu-id="b8d3c-116">Control.DefaultFont zmieniono na Segoe UI 9 pkt</span><span class="sxs-lookup"><span data-stu-id="b8d3c-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="b8d3c-117">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-117">3.0</span></span> |
| [<span data-ttu-id="b8d3c-118">Modernizacja folderuBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="b8d3c-118">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="b8d3c-119">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-119">3.0</span></span> |
| [<span data-ttu-id="b8d3c-120">SerializableAttribute usunięty z niektórych typów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8d3c-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="b8d3c-121">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-121">3.0</span></span> |
| [<span data-ttu-id="b8d3c-122">Przełącznik zgodności AllowUpdateChildControlIndexForTabControls nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-122">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-123">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-123">3.0</span></span> |
| [<span data-ttu-id="b8d3c-124">Przełącznik zgodności domainupdown.UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-124">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-125">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-125">3.0</span></span> |
| [<span data-ttu-id="b8d3c-126">Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-127">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-127">3.0</span></span> |
| [<span data-ttu-id="b8d3c-128">Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-128">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-129">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-129">3.0</span></span> |
| [<span data-ttu-id="b8d3c-130">Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-130">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-131">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-131">3.0</span></span> |
| [<span data-ttu-id="b8d3c-132">Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-132">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-133">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-133">3.0</span></span> |
| [<span data-ttu-id="b8d3c-134">Przełącznik zgodności UseLegacyContextMenuStripSourceControlValue nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-134">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-135">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-135">3.0</span></span> |
| [<span data-ttu-id="b8d3c-136">Przełącznik zgodności UseLegacyImages nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b8d3c-136">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="b8d3c-137">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-137">3.0</span></span> |
| [<span data-ttu-id="b8d3c-138">Zmiana dostępu dla AccessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="b8d3c-138">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="b8d3c-139">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-139">3.0</span></span> |
| [<span data-ttu-id="b8d3c-140">Zduplikowane interfejsy API usunięte z formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b8d3c-140">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="b8d3c-141">3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-141">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="b8d3c-142">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-142">.NET 5.0</span></span>

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="b8d3c-143">.NET Rdzeń 3.1</span><span class="sxs-lookup"><span data-stu-id="b8d3c-143">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="b8d3c-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b8d3c-144">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b8d3c-145">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b8d3c-145">See also</span></span>

- [<span data-ttu-id="b8d3c-146">Przenoszenie aplikacji Formularze systemu Windows do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="b8d3c-146">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
