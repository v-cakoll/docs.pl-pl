---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888138"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizacja folderuBrowserDialog

Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.

#### <a name="change-description"></a>Zmień opis

W programie .NET Framework formularze systemu Windows <xref:System.Windows.Forms.FolderBrowserDialog> używają następującego okna dialogowego dla formantu:

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

W programie .NET Core 3.0 użytkownicy formularzy systemu Windows nowszą formantem opartym na komisacie, który został wprowadzony w systemie Windows Vista:

![FolderBrowserDialogControl w rdzeniu .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Wprowadzono wersję

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Okno dialogowe zostanie uaktualnione automatycznie.

Jeśli chcesz zachować oryginalne okno <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> dialogowe, ustaw właściwość `false` przed wyświetleniem okna dialogowego, jak pokazano w następującym fragmencie kodu:

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

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
