---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643964"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="944bc-101">Modernizacja folderuOkno przeglądarki</span><span class="sxs-lookup"><span data-stu-id="944bc-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="944bc-102">Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach formularzy systemu Windows dla .NET Core.</span><span class="sxs-lookup"><span data-stu-id="944bc-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="944bc-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="944bc-103">Change description</span></span>

<span data-ttu-id="944bc-104">W programie .NET Framework formularze systemu <xref:System.Windows.Forms.FolderBrowserDialog> Windows używają następującego okna dialogowego dla formantu:</span><span class="sxs-lookup"><span data-stu-id="944bc-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![Formant FolderBrowserDialogControl w ramach .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="944bc-106">W programie .NET Core 3.0 użytkownicy formularzy systemu Windows mają nowszą kontrolę opartą na komisie, która została wprowadzona w systemie Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="944bc-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![Kontrola folderuDialogControl w rdzeniu .NET](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="944bc-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="944bc-108">Version introduced</span></span>

<span data-ttu-id="944bc-109">3.0</span><span class="sxs-lookup"><span data-stu-id="944bc-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="944bc-110">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="944bc-110">Recommended action</span></span>

<span data-ttu-id="944bc-111">Okno dialogowe zostanie automatycznie uaktualnione.</span><span class="sxs-lookup"><span data-stu-id="944bc-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="944bc-112">Jeśli chcesz zachować oryginalne okno dialogowe, ustaw <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> właściwość przed `false` wyświetleniem okna dialogowego, jak pokazano w następującym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="944bc-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="944bc-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="944bc-113">Category</span></span>

<span data-ttu-id="944bc-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="944bc-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="944bc-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="944bc-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
