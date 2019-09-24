---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217025"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="19ab6-101">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="19ab6-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="19ab6-102"><xref:System.Windows.Forms.FolderBrowserDialog> Formant został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="19ab6-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="19ab6-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="19ab6-103">Change description</span></span>

<span data-ttu-id="19ab6-104">W .NET Framework formularze systemu Windows używają następującego okna dialogowego dla <xref:System.Windows.Forms.FolderBrowserDialog> kontrolki:</span><span class="sxs-lookup"><span data-stu-id="19ab6-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="19ab6-106">W programie .NET Core 3,0 Użytkownicy Windows Formsą nowszą kontrolkę opartą na modelu COM wprowadzoną w systemie Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="19ab6-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl w programie .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="19ab6-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="19ab6-108">Version introduced</span></span>

<span data-ttu-id="19ab6-109">3.0</span><span class="sxs-lookup"><span data-stu-id="19ab6-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="19ab6-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="19ab6-110">Recommended action</span></span>

<span data-ttu-id="19ab6-111">Okno dialogowe zostanie uaktualnione automatycznie.</span><span class="sxs-lookup"><span data-stu-id="19ab6-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="19ab6-112">Jeśli chcesz zachować oryginalne okno dialogowe, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> właściwość na `false` przed wyświetleniem okna dialogowego, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="19ab6-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="19ab6-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="19ab6-113">Category</span></span>

<span data-ttu-id="19ab6-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="19ab6-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="19ab6-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="19ab6-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
