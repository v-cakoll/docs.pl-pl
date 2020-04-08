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
# <a name="breaking-changes-in-windows-forms"></a>Łamanie zmian w formularzach systemu Windows

Obsługa formularzy systemu Windows została dodana do platformy .NET Core w wersji 3.0. W tym artykule wymieniono przełomowe zmiany dla formularzy systemu Windows według wersji .NET Core, w której zostały wprowadzone. Jeśli uaktualniasz aplikację Formularze systemu Windows z programu .NET Framework lub z poprzedniej wersji programu .NET Core (3.0 lub nowszej), ten artykuł ma zastosowanie do Ciebie.

Na tej stronie są udokumentowane następujące zmiany podziału:

| Przełomowa zmiana | Wprowadzono wersję |
| - | :-: |
| [Interfejsy API WinForms teraz rzucać ArgumentNullException](#winforms-apis-now-throw-argumentnullexception) | 5.0 |
| [Usunięto kontrolki](#removed-controls) | 3.1 |
| [Zdarzenie CellFormatting nie jest wywoływane, jeśli wyświetlana jest etykietka narzędzia](#cellformatting-event-not-raised-if-tooltip-is-shown) | 3.1 |
| [Control.DefaultFont zmieniono na Segoe UI 9 pkt](#default-control-font-changed-to-segoe-ui-9-pt) | 3.0 |
| [Modernizacja folderuBrowserDialog](#modernization-of-the-folderbrowserdialog) | 3.0 |
| [SerializableAttribute usunięty z niektórych typów formularzy systemu Windows](#serializableattribute-removed-from-some-windows-forms-types) | 3.0 |
| [Przełącznik zgodności AllowUpdateChildControlIndexForTabControls nie jest obsługiwany](#allowupdatechildcontrolindexfortabcontrols-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności domainupdown.UseLegacyScrolling nie jest obsługiwany](#domainupdownuselegacyscrolling-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności DoNotLoadLatestRichEditControl nie jest obsługiwany](#donotloadlatestricheditcontrol-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności DoNotSupportSelectAllShortcutInMultilineTextBox nie jest obsługiwany](#donotsupportselectallshortcutinmultilinetextbox-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności DontSupportReentrantFilterMessage nie jest obsługiwany](#dontsupportreentrantfiltermessage-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności EnableVisualStyleValidation nie jest obsługiwany](#enablevisualstylevalidation-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności UseLegacyContextMenuStripSourceControlValue nie jest obsługiwany](#uselegacycontextmenustripsourcecontrolvalue-compatibility-switch-not-supported) | 3.0 |
| [Przełącznik zgodności UseLegacyImages nie jest obsługiwany](#uselegacyimages-compatibility-switch-not-supported) | 3.0 |
| [Zmiana dostępu dla AccessibleObject.RuntimeIDFirstItem](#change-of-access-for-accessibleobjectruntimeidfirstitem) | 3.0 |
| [Zduplikowane interfejsy API usunięte z formularzy systemu Windows](#duplicated-apis-removed-from-windows-forms) | 3.0 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [null-args-cause-argumentnullexception](../../../includes/core-changes/windowsforms/5.0/null-args-cause-argumentnullexception.md)]

***

## <a name="net-core-31"></a>.NET Rdzeń 3.1

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

- [Przenoszenie aplikacji Formularze systemu Windows do programu .NET Core](../porting/winforms.md)
