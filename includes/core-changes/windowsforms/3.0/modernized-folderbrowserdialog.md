---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643964"
---
### <a name="modernization-of-the-folderbrowserdialog"></a>Modernizacja folderuOkno przeglądarki

Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach formularzy systemu Windows dla .NET Core.

#### <a name="change-description"></a>Zmień opis

W programie .NET Framework formularze systemu <xref:System.Windows.Forms.FolderBrowserDialog> Windows używają następującego okna dialogowego dla formantu:

![Formant FolderBrowserDialogControl w ramach .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

W programie .NET Core 3.0 użytkownicy formularzy systemu Windows mają nowszą kontrolę opartą na komisie, która została wprowadzona w systemie Windows Vista:

![Kontrola folderuDialogControl w rdzeniu .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Okno dialogowe zostanie automatycznie uaktualnione.

Jeśli chcesz zachować oryginalne okno dialogowe, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> właściwość przed `false` wyświetleniem okna dialogowego, jak pokazano w następującym fragmencie kodu:

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
