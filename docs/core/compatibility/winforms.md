---
title: Windows Forms istotne zmiany
description: Wyświetla listę istotnych zmian w Windows Forms dla platformy .NET Core.
ms.date: 01/08/2020
ms.openlocfilehash: 75d369c7fb999da81a50fe46716e125c3840eb7a
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158440"
---
# <a name="breaking-changes-in-windows-forms"></a><span data-ttu-id="51d18-103">Istotne zmiany w Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51d18-103">Breaking changes in Windows Forms</span></span>

<span data-ttu-id="51d18-104">Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="51d18-104">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="51d18-105">W tym artykule wymieniono istotne zmiany Windows Forms przez wersję programu .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="51d18-105">This article lists breaking changes for Windows Forms by the .NET Core version in which they were introduced.</span></span> <span data-ttu-id="51d18-106">W przypadku uaktualniania aplikacji Windows Forms z .NET Framework lub poprzedniej wersji platformy .NET Core (3,0 lub nowszej) ten artykuł dotyczy Ciebie.</span><span class="sxs-lookup"><span data-stu-id="51d18-106">If you're upgrading a Windows Forms app from .NET Framework or from a previous version of .NET Core (3.0 or later), this article is applicable to you.</span></span>

<span data-ttu-id="51d18-107">Następujące istotne zmiany zostały udokumentowane na tej stronie:</span><span class="sxs-lookup"><span data-stu-id="51d18-107">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="51d18-108">Zmiana podziału</span><span class="sxs-lookup"><span data-stu-id="51d18-108">Breaking change</span></span> | <span data-ttu-id="51d18-109">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="51d18-109">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="51d18-110">Usunięto kontrolki paska stanu</span><span class="sxs-lookup"><span data-stu-id="51d18-110">Removed status bar controls</span></span>](#removed-status-bar-controls) | <span data-ttu-id="51d18-111">5.0</span><span class="sxs-lookup"><span data-stu-id="51d18-111">5.0</span></span> |
| [<span data-ttu-id="51d18-112">Metody WinForms teraz generują ArgumentException</span><span class="sxs-lookup"><span data-stu-id="51d18-112">WinForms methods now throw ArgumentException</span></span>](#winforms-methods-now-throw-argumentexception) | <span data-ttu-id="51d18-113">5.0</span><span class="sxs-lookup"><span data-stu-id="51d18-113">5.0</span></span> |
| [<span data-ttu-id="51d18-114">Metody WinForms teraz generują ArgumentNullException</span><span class="sxs-lookup"><span data-stu-id="51d18-114">WinForms methods now throw ArgumentNullException</span></span>](#winforms-methods-now-throw-argumentnullexception) | <span data-ttu-id="51d18-115">5.0</span><span class="sxs-lookup"><span data-stu-id="51d18-115">5.0</span></span> |
| [<span data-ttu-id="51d18-116">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="51d18-116">Removed controls</span></span>](#removed-controls) | <span data-ttu-id="51d18-117">3.1</span><span class="sxs-lookup"><span data-stu-id="51d18-117">3.1</span></span> |
| [<span data-ttu-id="51d18-118">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="51d18-118">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown) | <span data-ttu-id="51d18-119">3.1</span><span class="sxs-lookup"><span data-stu-id="51d18-119">3.1</span></span> |
| [<span data-ttu-id="51d18-120">Formant. DefaultFont został zmieniony na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="51d18-120">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt) | <span data-ttu-id="51d18-121">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-121">3.0</span></span> |
| [<span data-ttu-id="51d18-122">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="51d18-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog) | <span data-ttu-id="51d18-123">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-123">3.0</span></span> |
| [<span data-ttu-id="51d18-124">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51d18-124">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types) | <span data-ttu-id="51d18-125">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-125">3.0</span></span> |
| [<span data-ttu-id="51d18-126">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="51d18-126">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | <span data-ttu-id="51d18-127">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-127">3.0</span></span> |
| [<span data-ttu-id="51d18-128">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="51d18-128">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | <span data-ttu-id="51d18-129">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-129">3.0</span></span> |
| [<span data-ttu-id="51d18-130">Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="51d18-130">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | <span data-ttu-id="51d18-131">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-131">3.0</span></span> |
| [<span data-ttu-id="51d18-132">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="51d18-132">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | <span data-ttu-id="51d18-133">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-133">3.0</span></span> |
| [<span data-ttu-id="51d18-134">Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="51d18-134">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | <span data-ttu-id="51d18-135">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-135">3.0</span></span> |
| [<span data-ttu-id="51d18-136">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="51d18-136">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported) | <span data-ttu-id="51d18-137">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-137">3.0</span></span> |
| [<span data-ttu-id="51d18-138">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="51d18-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | <span data-ttu-id="51d18-139">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-139">3.0</span></span> |
| [<span data-ttu-id="51d18-140">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="51d18-140">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported) | <span data-ttu-id="51d18-141">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-141">3.0</span></span> |
| [<span data-ttu-id="51d18-142">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="51d18-142">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem) | <span data-ttu-id="51d18-143">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-143">3.0</span></span> |
| [<span data-ttu-id="51d18-144">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="51d18-144">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms) | <span data-ttu-id="51d18-145">3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-145">3.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="51d18-146">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="51d18-146">.NET 5.0</span></span>

[!INCLUDE [winforms-deprecated-controls](../../../includes/core-changes/windowsforms/5.0/winforms-deprecated-controls.md)]

***

[!INCLUDE [invalid-args-cause-argumentexception](../../../includes/core-changes/windowsforms/5.0/invalid-args-cause-argumentexception.md)]

***

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a><span data-ttu-id="51d18-147">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="51d18-147">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="51d18-148">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="51d18-148">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="51d18-149">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="51d18-149">See also</span></span>

- [<span data-ttu-id="51d18-150">Port aplikacji Windows Forms do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="51d18-150">Port a Windows Forms app to .NET Core</span></span>](../porting/winforms.md)
