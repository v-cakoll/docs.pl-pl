---
title: Przełomowe zmiany — .NET Framework do .NET Core
titleSuffix: ''
description: Wyświetla listę zmian krytycznych z programu .NET Framework na program .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: f712be14d7debc4b3008f8459e6ee925754b25f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449409"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a><span data-ttu-id="06775-103">Przełomowe zmiany migracji z platformy .NET Framework do programu .NET Core</span><span class="sxs-lookup"><span data-stu-id="06775-103">Breaking changes for migration from .NET Framework to .NET Core</span></span>

<span data-ttu-id="06775-104">Jeśli przeprowadzasz migrację aplikacji z platformy .NET Framework do platformy .NET Core, mogą mieć wpływ na zmiany dotyczące łamania, które są wymienione w tym artykule.</span><span class="sxs-lookup"><span data-stu-id="06775-104">If you're migrating an app from .NET Framework to .NET Core, the breaking changes listed in this article may affect you.</span></span> <span data-ttu-id="06775-105">Zmiany krytyczne są pogrupowane według kategorii i w ramach tych kategorii według wersji programu .NET Core, w której zostały wprowadzone.</span><span class="sxs-lookup"><span data-stu-id="06775-105">Breaking changes are grouped by category, and within those categories, by the version of .NET Core in which they were introduced.</span></span>

> [!NOTE]
> <span data-ttu-id="06775-106">Ten artykuł nie jest pełną listą zmian między programami .NET Framework a .NET Core.</span><span class="sxs-lookup"><span data-stu-id="06775-106">This article is not a complete list of breaking changes between .NET Framework and .NET Core.</span></span> <span data-ttu-id="06775-107">Najważniejsze przełomowe zmiany są dodawane tutaj, gdy dowiemy się o nich.</span><span class="sxs-lookup"><span data-stu-id="06775-107">The most important breaking changes are added here as we become aware of them.</span></span>

## <a name="corefx"></a><span data-ttu-id="06775-108">CoreFx</span><span class="sxs-lookup"><span data-stu-id="06775-108">CoreFx</span></span>

- [<span data-ttu-id="06775-109">Zmiana wartości domyślnej programu UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="06775-109">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute)
- [<span data-ttu-id="06775-110">UnauthorizedAccessException zgłoszony przez FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="06775-110">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a><span data-ttu-id="06775-111">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="06775-111">.NET Core 2.1</span></span>

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a><span data-ttu-id="06775-112">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="06775-112">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a><span data-ttu-id="06775-113">Kryptografia</span><span class="sxs-lookup"><span data-stu-id="06775-113">Cryptography</span></span>

- [<span data-ttu-id="06775-114">Przestrzegany jest parametr logiczny podpisu SignedCms.ComputeSignature</span><span class="sxs-lookup"><span data-stu-id="06775-114">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a><span data-ttu-id="06775-115">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="06775-115">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a><span data-ttu-id="06775-116">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="06775-116">Windows Forms</span></span>

<span data-ttu-id="06775-117">Obsługa formularzy systemu Windows została dodana do programu .NET Core w wersji 3.0.</span><span class="sxs-lookup"><span data-stu-id="06775-117">Windows Forms support was added to .NET Core in version 3.0.</span></span> <span data-ttu-id="06775-118">Jeśli przeprowadzasz migrację aplikacji Formularze systemu Windows z platformy .NET Framework do platformy .NET Core, zmiany powodujące następujące następujące zmiany mogą mieć wpływ na aplikację.</span><span class="sxs-lookup"><span data-stu-id="06775-118">If you're migrating a Windows Forms app from .NET Framework to .NET Core, the breaking changes listed here may affect your app.</span></span>

- [<span data-ttu-id="06775-119">Usunięte formanty</span><span class="sxs-lookup"><span data-stu-id="06775-119">Removed controls</span></span>](#removed-controls)
- [<span data-ttu-id="06775-120">Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia</span><span class="sxs-lookup"><span data-stu-id="06775-120">CellFormatting event not raised if tooltip is shown</span></span>](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [<span data-ttu-id="06775-121">Control.DefaultFont zmieniono na Segoe UI 9 pkt</span><span class="sxs-lookup"><span data-stu-id="06775-121">Control.DefaultFont changed to Segoe UI 9 pt</span></span>](#default-control-font-changed-to-segoe-ui-9-pt)
- [<span data-ttu-id="06775-122">Modernizacja folderuOkno przeglądarki</span><span class="sxs-lookup"><span data-stu-id="06775-122">Modernization of the FolderBrowserDialog</span></span>](#modernization-of-the-folderbrowserdialog)
- [<span data-ttu-id="06775-123">SerializableAttribute usunięte z niektórych typów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="06775-123">SerializableAttribute removed from some Windows Forms types</span></span>](#serializableattribute-removed-from-some-windows-forms-types)
- [<span data-ttu-id="06775-124">Przełącznik zgodności AllowUpdateChildControlForTabControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-124">AllowUpdateChildControlIndexForTabControls compatibility switch not supported</span></span>](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-125">Przełącznik zgodności DomainUpDown.UseLegacyScrolling nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-125">DomainUpDown.UseLegacyScrolling compatibility switch not supported</span></span>](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-126">Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-126">DoNotLoadLatestRichEditControl compatibility switch not supported</span></span>](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-127">Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-127">DoNotSupportSelectAllShortcutInMultilineTextBox compatibility switch not supported</span></span>](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-128">Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-128">DontSupportReentrantFilterMessage compatibility switch not supported</span></span>](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-129">Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-129">EnableVisualStyleValidation compatibility switch not supported</span></span>](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-130">UseLegacyContextMenuStripSourceControlValue przełącznik zgodności nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-130">UseLegacyContextMenuStripSourceControlValue compatibility switch not supported</span></span>](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-131">Przełącznik zgodności UseLegacyImages nie jest obsługiwany</span><span class="sxs-lookup"><span data-stu-id="06775-131">UseLegacyImages compatibility switch not supported</span></span>](#uselegacyimages-compatibility-switch-not-supported)
- [<span data-ttu-id="06775-132">Zmiana dostępu dla accessibleObject.RuntimeIDFirstItem</span><span class="sxs-lookup"><span data-stu-id="06775-132">Change of access for AccessibleObject.RuntimeIDFirstItem</span></span>](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [<span data-ttu-id="06775-133">Zduplikowane interfejsy API usunięte z formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="06775-133">Duplicated APIs removed from Windows Forms</span></span>](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a><span data-ttu-id="06775-134">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="06775-134">.NET Core 3.1</span></span>

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a><span data-ttu-id="06775-135">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="06775-135">.NET Core 3.0</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06775-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="06775-136">See also</span></span>

- [<span data-ttu-id="06775-137">Interfejsy API, które zawsze zgłaszają wyjątki w uspolonym .NET Core</span><span class="sxs-lookup"><span data-stu-id="06775-137">APIs that always throw exceptions on .NET Core</span></span>](unsupported-apis.md)
- [<span data-ttu-id="06775-138">Technologie .NET Framework niedostępne w platformie .NET Core</span><span class="sxs-lookup"><span data-stu-id="06775-138">.NET Framework technologies unavailable on .NET Core</span></span>](../porting/net-framework-tech-unavailable.md)
