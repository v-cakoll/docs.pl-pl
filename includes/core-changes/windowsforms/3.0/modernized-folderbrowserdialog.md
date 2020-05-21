---
ms.openlocfilehash: 11c04441dcec260f0bfb90f6ed2b919b1545b382
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721004"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="9d8ac-101">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="9d8ac-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="9d8ac-102"><xref:System.Windows.Forms.FolderBrowserDialog>Formant został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9d8ac-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="9d8ac-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="9d8ac-103">Change description</span></span>

<span data-ttu-id="9d8ac-104">W .NET Framework formularze systemu Windows używają następującego okna dialogowego dla <xref:System.Windows.Forms.FolderBrowserDialog> kontrolki:</span><span class="sxs-lookup"><span data-stu-id="9d8ac-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="9d8ac-106">W programie .NET Core 3,0 Użytkownicy Windows Formsą nowszą kontrolkę opartą na modelu COM wprowadzoną w systemie Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="9d8ac-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl w programie .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="9d8ac-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="9d8ac-108">Version introduced</span></span>

<span data-ttu-id="9d8ac-109">3.0</span><span class="sxs-lookup"><span data-stu-id="9d8ac-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="9d8ac-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="9d8ac-110">Recommended action</span></span>

<span data-ttu-id="9d8ac-111">Okno dialogowe zostanie uaktualnione automatycznie.</span><span class="sxs-lookup"><span data-stu-id="9d8ac-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="9d8ac-112">Jeśli chcesz zachować oryginalne okno dialogowe, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> Właściwość na `false` przed wyświetleniem okna dialogowego, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="9d8ac-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="9d8ac-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="9d8ac-113">Category</span></span>

<span data-ttu-id="9d8ac-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9d8ac-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="9d8ac-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="9d8ac-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

#### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
