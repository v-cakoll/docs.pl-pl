---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643964"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizacja FolderBrowserDialog

Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.

#### <a name="change-description"></a>Zmień opis

W .NET Framework formularzy systemu Windows używa następującego okna dialogowego dla kontrolki <xref:System.Windows.Forms.FolderBrowserDialog>:

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

W programie .NET Core 3,0 Użytkownicy Windows Formsą nowszą kontrolkę opartą na modelu COM wprowadzoną w systemie Windows Vista:

![FolderBrowserDialogControl w programie .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Okno dialogowe zostanie uaktualnione automatycznie.

Aby zachować pierwotne okno dialogowe, należy ustawić właściwość <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> na `false` przed wyświetleniem okna dialogowego, jak pokazano w poniższym fragmencie kodu:

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
