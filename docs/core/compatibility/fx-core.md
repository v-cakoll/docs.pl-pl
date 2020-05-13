---
title: Istotne zmiany — .NET Framework do platformy .NET Core
titleSuffix: ''
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: 613c4e41e12be57d5631b347055140a4418e7207
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83206461"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="b1cb6-103">Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1cb6-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="b1cb6-104">W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="b1cb6-105">Istotne zmiany są pogrupowane według kategorii i w ramach tych kategorii według wersji platformy .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="b1cb6-106">Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="b1cb6-107">Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="core-net-libraries"></a><span data-ttu-id="b1cb6-108">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="b1cb6-108">Core .NET libraries</span></span>

- [<span data-ttu-id="b1cb6-109">Zmień wartość domyślną UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="b1cb6-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="b1cb6-110">UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="b1cb6-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [<span data-ttu-id="b1cb6-111">Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="b1cb6-111">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported)
- [<span data-ttu-id="b1cb6-112">Właściwości UriBuilder nie dołączają już znaków wiodących</span><span class="sxs-lookup"><span data-stu-id="b1cb6-112">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters)

### <a name="net-core-21"></a><span data-ttu-id="b1cb6-113">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b1cb6-113">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="b1cb6-114">.NET Core 1,0</span><span class="sxs-lookup"><span data-stu-id="b1cb6-114">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

## <a name="cryptography"></a><span data-ttu-id="b1cb6-115">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="b1cb6-115">Cryptography</span></span>

- [<span data-ttu-id="b1cb6-116">Parametr logiczny elementu SignedCms. ComputeSignature jest przestrzegany</span><span class="sxs-lookup"><span data-stu-id="b1cb6-116">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="b1cb6-117">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="b1cb6-117">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a><span data-ttu-id="b1cb6-118">MSBuild</span><span class="sxs-lookup"><span data-stu-id="b1cb6-118">MSBuild</span></span>

- [<span data-ttu-id="b1cb6-119">Zmiana nazwy pliku manifestu zasobu</span><span class="sxs-lookup"><span data-stu-id="b1cb6-119">Resource manifest file name change</span></span>](#resource-manifest-file-name-change)

### <a name="net-core-30"></a><span data-ttu-id="b1cb6-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1cb6-120">.NET Core 3.0</span></span>

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a><span data-ttu-id="b1cb6-121">Networking</span><span class="sxs-lookup"><span data-stu-id="b1cb6-121">Networking</span></span>

- [<span data-ttu-id="b1cb6-122">Klient WebClient. CancelAsync nie zawsze anuluje natychmiast</span><span class="sxs-lookup"><span data-stu-id="b1cb6-122">WebClient.CancelAsync doesn't always cancel immediately</span></span>](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a><span data-ttu-id="b1cb6-123">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="b1cb6-123">.NET Core 2.0</span></span>

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="b1cb6-124">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1cb6-124">Windows Forms</span></span>

<span data-ttu-id="b1cb6-125">Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-125">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="b1cb6-126">W przypadku migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core zmiany wymienione w tym miejscu mogą mieć wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="b1cb6-126">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="b1cb6-127">Usunięte kontrolki</span><span class="sxs-lookup"><span data-stu-id="b1cb6-127">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="b1cb6-128">Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="b1cb6-128">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="b1cb6-129">Formant. DefaultFont został zmieniony na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="b1cb6-129">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="b1cb6-130">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="b1cb6-130">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="b1cb6-131">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1cb6-131">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="b1cb6-132">Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls</span><span class="sxs-lookup"><span data-stu-id="b1cb6-132">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-133">Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="b1cb6-133">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-134">Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl</span><span class="sxs-lookup"><span data-stu-id="b1cb6-134">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-135">Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox</span><span class="sxs-lookup"><span data-stu-id="b1cb6-135">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-136">Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage</span><span class="sxs-lookup"><span data-stu-id="b1cb6-136">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-137">Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation</span><span class="sxs-lookup"><span data-stu-id="b1cb6-137">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-138">Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue</span><span class="sxs-lookup"><span data-stu-id="b1cb6-138">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-139">Nieobsługiwany przełącznik zgodności UseLegacyImages</span><span class="sxs-lookup"><span data-stu-id="b1cb6-139">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="b1cb6-140">Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="b1cb6-140">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="b1cb6-141">Zduplikowane interfejsy API zostały usunięte z Windows Forms</span><span class="sxs-lookup"><span data-stu-id="b1cb6-141">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="b1cb6-142">.NET Core 3,1</span><span class="sxs-lookup"><span data-stu-id="b1cb6-142">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="b1cb6-143">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="b1cb6-143">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1cb6-144">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b1cb6-144">See also</span></span>

- [<span data-ttu-id="b1cb6-145">Interfejsy API, które zawsze generują wyjątki w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1cb6-145">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="b1cb6-146">Technologie .NET Framework niedostępne w programie .NET Core</span><span class="sxs-lookup"><span data-stu-id="b1cb6-146">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
