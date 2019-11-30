---
ms.openlocfilehash: 24141f4b95cda2ae382a923da034e75c329b8555
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643964"
---
### <a name="modernization-of-the-folderbrowserdialog"></a><span data-ttu-id="12a37-101">Modernizacja FolderBrowserDialog</span><span class="sxs-lookup"><span data-stu-id="12a37-101">Modernization of the FolderBrowserDialog</span></span>

<span data-ttu-id="12a37-102">Formant <xref:System.Windows.Forms.FolderBrowserDialog> został zmieniony w aplikacjach Windows Forms dla platformy .NET Core.</span><span class="sxs-lookup"><span data-stu-id="12a37-102">The <xref:System.Windows.Forms.FolderBrowserDialog> control has changed in Windows Forms applications for .NET Core.</span></span>

#### <a name="change-description"></a><span data-ttu-id="12a37-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="12a37-103">Change description</span></span>

<span data-ttu-id="12a37-104">W .NET Framework formularzy systemu Windows używa następującego okna dialogowego dla kontrolki <xref:System.Windows.Forms.FolderBrowserDialog>:</span><span class="sxs-lookup"><span data-stu-id="12a37-104">In the .NET Framework, Windows forms uses the following dialog for the <xref:System.Windows.Forms.FolderBrowserDialog> control:</span></span>

![FolderBrowserDialogControl w .NET Framework](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-framework.png)

<span data-ttu-id="12a37-106">W programie .NET Core 3,0 Użytkownicy Windows Formsą nowszą kontrolkę opartą na modelu COM wprowadzoną w systemie Windows Vista:</span><span class="sxs-lookup"><span data-stu-id="12a37-106">In .NET Core 3.0, Windows Forms users a newer COM-based control that was introduced in Windows Vista:</span></span>

![FolderBrowserDialogControl w programie .NET Core](~/docs/images/core-changes/windowsforms/modernized-folderbrowserdialog/folderdlg-core.png)

#### <a name="version-introduced"></a><span data-ttu-id="12a37-108">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="12a37-108">Version introduced</span></span>

<span data-ttu-id="12a37-109">3.0</span><span class="sxs-lookup"><span data-stu-id="12a37-109">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="12a37-110">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="12a37-110">Recommended action</span></span>

<span data-ttu-id="12a37-111">Okno dialogowe zostanie uaktualnione automatycznie.</span><span class="sxs-lookup"><span data-stu-id="12a37-111">The dialog will be upgraded automatically.</span></span>

<span data-ttu-id="12a37-112">Aby zachować pierwotne okno dialogowe, należy ustawić właściwość <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> na `false` przed wyświetleniem okna dialogowego, jak pokazano w poniższym fragmencie kodu:</span><span class="sxs-lookup"><span data-stu-id="12a37-112">If you desire to retain the original dialog, set the <xref:System.Windows.Forms.FolderBrowserDialog.AutoUpgradeEnabled?displayProperty=nameWithType> property to `false` before showing the dialog, as illustrated by the following code fragment:</span></span>

```csharp
var dialog = new FolderBrowserDialog();
dialog.AutoUpgradeEnabled = false;
dialog.ShowDialog();
```

#### <a name="category"></a><span data-ttu-id="12a37-113">Kategoria</span><span class="sxs-lookup"><span data-stu-id="12a37-113">Category</span></span>

<span data-ttu-id="12a37-114">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="12a37-114">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="12a37-115">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="12a37-115">Affected APIs</span></span>

- <xref:System.Windows.Forms.FolderBrowserDialog>

<!--

### Affected APIs

- `System.Windows.Forms.FolderBrowserDialog`

-->
