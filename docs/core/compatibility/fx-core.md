---
title: Istotne zmiany — .NET Framework do platformy .NET Core
titleSuffix: ''
description: Wyświetla listę istotnych zmian z .NET Framework do programu .NET Core.
ms.date: 05/05/2020
ms.openlocfilehash: f830d4571f21752900b35a7462bf0881673d6d2e
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2020
ms.locfileid: "83420451"
---
# <a name="breaking-changes-for-migration-from-net-framework-to-net-core"></a>Istotne zmiany dotyczące migracji z .NET Framework do platformy .NET Core

W przypadku migrowania aplikacji z programu .NET Framework do programu .NET Core, istotne zmiany wymienione w tym artykule mogą mieć wpływ na użytkownika. Istotne zmiany są pogrupowane według kategorii i w ramach tych kategorii według wersji platformy .NET Core, w której zostały wprowadzone.

> [!NOTE]
> Ten artykuł nie jest pełną listą istotnych zmian między .NET Framework i .NET Core. Najważniejsze zmiany zostaną dodane w tym miejscu w miarę ich istnienia.

## <a name="core-net-libraries"></a>Podstawowe biblioteki platformy .NET

- [Zmień wartość domyślną UseShellExecute](#change-in-default-value-of-useshellexecute)
- [UnauthorizedAccessException zgłoszone przez FileSystemInfo. Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes)
- [Obsługa wyjątków uszkodzonego stanu procesu nie jest obsługiwana](#handling-corrupted-state-exceptions-is-not-supported)
- [Właściwości UriBuilder nie dołączają już znaków wiodących](#uribuilder-properties-no-longer-prepend-leading-characters)
- [Proces. element StartInfo zgłasza InvalidOperationException dla procesów, które nie zostały uruchomione](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Process.Start changes](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

### <a name="net-core-10"></a>.NET Core 1,0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***

## <a name="cryptography"></a>Kryptografia

- [Parametr logiczny elementu SignedCms. ComputeSignature jest przestrzegany](#boolean-parameter-of-signedcmscomputesignature-is-respected)

### <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***

## <a name="msbuild"></a>MSBuild

- [Zmiana nazwy pliku manifestu zasobu](#resource-manifest-file-name-change)

### <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[Resource file names](~/includes/core-changes/msbuild/3.0/resource-manifest-name.md)]

***

## <a name="networking"></a>Networking

- [Klient WebClient. CancelAsync nie zawsze anuluje natychmiast](#webclientcancelasync-doesnt-always-cancel-immediately)

### <a name="net-core-20"></a>.NET Core 2.0

[!INCLUDE [behavior-change-webclient-cancelasync](../../../includes/core-changes/networking/2.0/behavior-change-webclient-cancelasync.md)]

***

## <a name="windows-forms"></a>Windows Forms

Obsługa Windows Forms została dodana do programu .NET Core w wersji 3,0. W przypadku migrowania aplikacji Windows Forms z .NET Framework do platformy .NET Core zmiany wymienione w tym miejscu mogą mieć wpływ na aplikację.

- [Usunięte kontrolki](#removed-controls)
- [Zdarzenie CellFormatting nie zostało zgłoszone, jeśli jest wyświetlana etykietka narzędzia](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Formant. DefaultFont został zmieniony na Segoe UI 9 pt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizacja FolderBrowserDialog](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute usunięte z niektórych typów Windows Forms](#serializableattribute-removed-from-some-windows-forms-types)
- [Nieobsługiwany przełącznik zgodności AllowUpdateChildControlIndexForTabControls](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Przełącznik zgodności DomainUpDown. UseLegacyScrolling nie jest obsługiwany](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności DoNotLoadLatestRichEditControl](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności DontSupportReentrantFilterMessage](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności EnableVisualStyleValidation](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności UseLegacyContextMenuStripSourceControlValue](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Nieobsługiwany przełącznik zgodności UseLegacyImages](#uselegacyimages-compatibility-switch-not-supported)
- [Zmiana dostępu do elementu AccessibleObject. RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Zduplikowane interfejsy API zostały usunięte z Windows Forms](#duplicated-apis-removed-from-windows-forms)

### <a name="net-core-31"></a>.NET Core 3,1

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

## <a name="see-also"></a>Zobacz także

- [Interfejsy API, które zawsze generują wyjątki w programie .NET Core](unsupported-apis.md)
- [Technologie .NET Framework niedostępne w programie .NET Core](../porting/net-framework-tech-unavailable.md)
