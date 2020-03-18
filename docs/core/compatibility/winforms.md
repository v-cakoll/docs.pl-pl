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
# <a name="breaking-changes-in-windows-forms"></a>Krytyczne zmiany w formularzach systemu Windows

Obsługa formularzy systemu Windows została dodana do programu .NET Core w wersji 3.0. W tym artykule wymieniono zmiany dotyczące łamania formularzy systemu Windows według wersji .NET Core, w której zostały wprowadzone. Jeśli uaktualniasz aplikację Windows Forms z platformy .NET Framework lub z poprzedniej wersji programu .NET Core (3.0 lub nowszej), ten artykuł ma zastosowanie do użytkownika.

Na tej stronie udokumentowane są następujące zmiany dotyczące zasad:

- [Usunięte formanty](#removed-controls)
- [Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia](#cellformatting-event-not-raised-if-tooltip-is-shown)
- [Control.DefaultFont zmieniono na Segoe UI 9 pkt](#default-control-font-changed-to-segoe-ui-9-pt)
- [Modernizacja folderuOkno przeglądarki](#modernization-of-the-folderbrowserdialog)
- [SerializableAttribute usunięte z niektórych typów formularzy systemu Windows](#serializableattribute-removed-from-some-windows-forms-types)
- [Przełącznik zgodności AllowUpdateChildControlForTabControl nie jest obsługiwany](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported)
- [Przełącznik zgodności DomainUpDown.UseLegacyScrolling nie jest obsługiwany](#domainupdownuselegacyscrolling-compatibility-switch-not-supported)
- [Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany](#donotloadlatestricheditcontrol-compatibility-switch-not-supported)
- [Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported)
- [Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported)
- [Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany](#enablevisualstylevalidation-compatibility-switch-not-supported)
- [UseLegacyContextMenuStripSourceControlValue przełącznik zgodności nie jest obsługiwany](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported)
- [Przełącznik zgodności UseLegacyImages nie jest obsługiwany](#uselegacyimages-compatibility-switch-not-supported)
- [Zmiana dostępu dla accessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem)
- [Zduplikowane interfejsy API usunięte z formularzy systemu Windows](#duplicated-apis-removed-from-windows-forms)

## <a name="net-core-31"></a>.NET Core 3.1

[!INCLUDE[Removed controls](~/includes/core-changes/windowsforms/3.1/remove-controls-3.1.md)]

***

[!INCLUDE[CellFormatting event](~/includes/core-changes/windowsforms/3.1/cellformatting-event-not-raised.md)]

***

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="see-also"></a>Zobacz też

- [Przenoszenie aplikacji formularzy systemu Windows do usługi .NET Core](../porting/winforms.md)
