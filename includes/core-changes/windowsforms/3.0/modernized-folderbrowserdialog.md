---
ms.openlocfilehash: 645df8080abd21e4db95903a301a36b79a698858
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888138"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="74640-101">Modernizacja folderuBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="74640-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="74640-102">Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="74640-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="74640-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="74640-103">Change description</span></span>

<span data-ttu-id="74640-104">W programie .NET Framework formularze systemu Windows <xref:System.Windows.Forms.FolderBrowserDialog> używają następującego okna dialogowego dla formantu:</span><span class="sxs-lookup"><span data-stu-id="74640-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="74640-106">W programie .NET Core 3.0 użytkownicy formularzy systemu Windows nowszą formantem opartym na komisacie, który został wprowadzony w systemie Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="74640-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl w rdzeniu .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="74640-108">Wprowadzono wersję</span><span class="sxs-lookup"><span data-stu-id="74640-108">Version introduced</span></span>

<span data-ttu-id="74640-109">3.0</span><span class="sxs-lookup"><span data-stu-id="74640-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="74640-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="74640-110">Recommended action</span></span>

<span data-ttu-id="74640-111">Okno dialogowe zostanie uaktualnione automatycznie.</span><span class="sxs-lookup"><span data-stu-id="74640-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="74640-112">Jeśli chcesz zachować oryginalne okno <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> dialogowe, ustaw właściwość `false` przed wyświetleniem okna dialogowego, jak pokazano w następującym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="74640-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="74640-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="74640-113">Category</span></span>

<span data-ttu-id="74640-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="74640-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="74640-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="74640-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `T:System.Windows.Forms.FolderBrowserDialog`

-->
