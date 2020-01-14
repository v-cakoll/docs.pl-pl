---
title: Istotne zmiany — .NET Framework do platformy .NET Core
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: 9f4ecc8a9de7279bb4b222b3df77e1eb17b33f0a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75937393"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="9a3f2-103">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a3f2-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="9a3f2-104">W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="9a3f2-105">Istotne zmiany są pogrupowane według kategorii i w ramach tych kategorii według wersji programu .NET Core, która została wprowadzona w systemie.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core they were introduced in.</span></span>

> [!NOTE]
> <span data-ttu-id="9a3f2-106">Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="9a3f2-107">Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="9a3f2-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="9a3f2-108">CoreFx</span></span>

<span data-ttu-id="9a3f2-109">Zmiany powodujące niezgodność:</span><span class="sxs-lookup"><span data-stu-id="9a3f2-109">Breaking changes:</span></span>

- [<span data-ttu-id="9a3f2-110">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="9a3f2-110">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)

***

### <a name="net-core-21"></a><span data-ttu-id="9a3f2-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9a3f2-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="9a3f2-112">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a3f2-112">Windows Forms</span></span>

<span data-ttu-id="9a3f2-113">Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-113">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="9a3f2-114">W przypadku migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core zmiany wymienione w tym miejscu mogą mieć wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="9a3f2-114">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

<span data-ttu-id="9a3f2-115">Zmiany powodujące niezgodność:</span><span class="sxs-lookup"><span data-stu-id="9a3f2-115">Breaking changes:</span></span>

- [<span data-ttu-id="9a3f2-116">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="9a3f2-116">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="9a3f2-117">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="9a3f2-117">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="9a3f2-118">Formant. DefaultFont został zmieniony na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="9a3f2-118">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="9a3f2-119">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="9a3f2-119">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="9a3f2-120">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a3f2-120">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="9a3f2-121">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="9a3f2-121">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-122">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="9a3f2-122">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-123">Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="9a3f2-123">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-124">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="9a3f2-124">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-125">Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="9a3f2-125">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-126">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="9a3f2-126">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-127">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="9a3f2-127">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-128">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="9a3f2-128">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="9a3f2-129">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="9a3f2-129">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="9a3f2-130">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9a3f2-130">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="9a3f2-131">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="9a3f2-131">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="9a3f2-132">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9a3f2-132">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="9a3f2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a3f2-133">See also</span></span>

- [<span data-ttu-id="9a3f2-134">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a3f2-134">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="9a3f2-135">Technologie .NET Framework niedostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="9a3f2-135">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
