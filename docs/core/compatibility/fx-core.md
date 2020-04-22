---
title: Łamanie zmian — program .NET Framework to .NET Core
titleSuffix: ''
description: Wyświetla listę przełomowych zmian z programu .NET Framework na .NET Core.
ms.date: 12/18/2019
ms.openlocfilehash: ef16132c8dcffbe9bcfbe02834c9a78d6d0c33e4
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021787"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Przerywanie zmian migracji z programu .NET Framework do programu .NET Core

Jeśli przeprowadzasz migrację aplikacji z programu .NET Framework do platformy .NET Core, zmiany dotyczące podziału wymienione w tym artykule mogą mieć wpływ na Ciebie. Zmiany podziału są pogrupowane według kategorii i w ramach tych kategorii, według wersji .NET Core, w której zostały wprowadzone.

> [!NOTE]
> Ten artykuł nie jest pełną listą przełomowych zmian między programem .NET Framework a programem .NET Core. Najważniejsze przełomowe zmiany są dodawane tutaj, gdy stajemy się o nich świadomi.

## <a name="core-net-libraries"></a>Podstawowe biblioteki .NET

- [Zmiana wartości domyślnej UseShellExecute](#change-in-default-value-of-useshellexecute)
- [NieautoryzowaneaccessException generowane przez FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Rdzeń 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

## <a name="cryptography"></a>Kryptografia

- [Parametr logiczny signedcms.computesignature jest przestrzegany](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="windows-forms"></a>Windows Forms

Obsługa formularzy systemu Windows została dodana do platformy .NET Core w wersji 3.0. Jeśli przeprowadzasz migrację aplikacji Windows Forms z programu .NET Framework do platformy .NET Core, zmiany podziału wymienione w tym miejscu mogą mieć wpływ na aplikację.

- [Usunięto kontrolki](#removed-controls)
- [Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont zmieniono na Segoe UI 9 pkt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizacja folderuBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute usunięty z niektórych typów formularzy systemu Windows](#serializableattribute-removed-from-some-windows-forms-types)
- [Przełącznik zgodności AllowUpdateChildControlIndexForTabControls nie jest obsługiwany](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Przełącznik zgodności domainupdown.UseLegacyScrolling nie jest obsługiwany](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Przełącznik zgodności UseLegacyContextMenuStripSourceControlValue nie jest obsługiwany](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Przełącznik zgodności UseLegacyImages nie jest obsługiwany](#uselegacyimages-compatibility-switch-not-supported)
- [Zmiana dostępu dla AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Zduplikowane interfejsy API usunięte z formularzy systemu Windows](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Rdzeń 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

### <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Zobacz też

- [Interfejsy API, które zawsze zgłaszają wyjątki w programie .NET Core](unsupported-apis.md)
- [Technologie .NET Framework są niedostępne w programie .NET Core](../porting/net-framework-tech-unavailable.md)
