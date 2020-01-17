---
title: Istotne zmiany — .NET Framework do platformy .NET Core
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 6959bffab62cabc524062231db989de45c8c1498
ms.sourcegitcommit: ed3f926b6cdd372037bbcc214dc8f08a70366390
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2020
ms.locfileid: "76116491"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="079fb-103">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="079fb-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="079fb-104">W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="079fb-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="079fb-105">Istotne zmiany są pogrupowane według kategorii i w ramach tych kategorii według wersji programu .NET Core, która została wprowadzona w systemie.</span><span class="sxs-lookup"><span data-stu-id="079fb-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="079fb-106">Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="079fb-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="079fb-107">Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.</span><span class="sxs-lookup"><span data-stu-id="079fb-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="079fb-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="079fb-108">CoreFx</span></span>

- [<span data-ttu-id="079fb-109">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="079fb-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

### <a name="net-core-21"></a><span data-ttu-id="079fb-110">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="079fb-110">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="079fb-111">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="079fb-111">Windows Forms</span></span>

<span data-ttu-id="079fb-112">Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="079fb-112">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="079fb-113">W przypadku migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core zmiany wymienione w tym miejscu mogą mieć wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="079fb-113">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="079fb-114">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="079fb-114">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="079fb-115">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="079fb-115">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="079fb-116">Formant. DefaultFont został zmieniony na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="079fb-116">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="079fb-117">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="079fb-117">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="079fb-118">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="079fb-118">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="079fb-119">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="079fb-119">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-120">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="079fb-120">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-121">Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="079fb-121">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-122">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="079fb-122">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-123">Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="079fb-123">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-124">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="079fb-124">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-125">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="079fb-125">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-126">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="079fb-126">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="079fb-127">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="079fb-127">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="079fb-128">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="079fb-128">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="079fb-129">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="079fb-129">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="079fb-130">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="079fb-130">.NET Core 3.0</span></span>

[!INCLUDE[Control.DefaultFont changed to Segoe UI 9 pt](~/includes/core-changes/windowsforms/3.0/control-defaultfont-changed.md)]

***

[!INCLUDE[Modernization of the FolderBrowserDialog](~/includes/core-changes/windowsforms/3.0/modernized-folderbrowserdialog.md)]

***

[!INCLUDE[SerializableAttribute removed from some Windows Forms types](~/includes/core-changes/windowsforms/3.0/remove-serializationattribute.md)]

***

[!INCLUDE[AllowUpdateChildControlIndexForTabControls compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-allowupdatechildcontrolindexfortabcontrols.md)]

***

[!INCLUDE[DomainUpDown.UseLegacyScrolling compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyscrolling.md)]

***

[!INCLUDE[DoNotLoadLatestRichEditControl compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotloadlatestricheditcontrol.md)]

***

[!INCLUDE[DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-donotsupportselectallshortcutinmultilinetextbox.md)]

***

[!INCLUDE[DontSupportReentrantFilterMessage compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-dontsupportreentrantfiltermessage.md)]

***

[!INCLUDE[EnableVisualStyleValidation compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-enablevisualstylevalidation.md)]

***

[!INCLUDE[UseLegacyContextMenuStripSourceControlValue compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacycontextmenustripsourcecontrolvalue.md)]

***

[!INCLUDE[UseLegacyImages compatibility switch not supported](~/includes/core-changes/windowsforms/3.0/deprecate-uselegacyimages.md)]

***

[!INCLUDE[Change of access for AccessibleObject.RuntimeIDFirstItem](~/includes/core-changes/windowsforms/3.0/changed-access-for-runtimeidfirstitem.md)]

***

[!INCLUDE[Duplicated APIs removed from Windows Forms](~/includes/core-changes/windowsforms/3.0/remove-duplicated-apis.md)]

***

## <a name="see-also"></a><span data-ttu-id="079fb-131">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="079fb-131">See also</span></span>

- [<span data-ttu-id="079fb-132">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="079fb-132">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="079fb-133">Technologie .NET Framework niedostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="079fb-133">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
