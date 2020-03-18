---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936996"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="ee3c7-101">Domyślna czcionka kontrolna zmieniona na Segoe UI 9 pkt</span><span class="sxs-lookup"><span data-stu-id="ee3c7-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="ee3c7-102">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="ee3c7-102">Change description</span></span>

<span data-ttu-id="ee3c7-103">W platformie <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> .NET Framework `Microsoft Sans Serif 8 pt`właściwość została ustawiona na .</span><span class="sxs-lookup"><span data-stu-id="ee3c7-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ee3c7-104">Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ee3c7-104">The following image shows a window that uses the default font.</span></span>

![Domyślna czcionka kontrolna w programach .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="ee3c7-106">Począwszy od .NET Core 3.0, `Segoe UI 9 pt` domyślna czcionka <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>jest ustawiona na (ta sama czcionka co ).</span><span class="sxs-lookup"><span data-stu-id="ee3c7-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="ee3c7-107">W wyniku tej zmiany formularze i formanty są o 27% większe, aby uwzględnić większy rozmiar nowej czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="ee3c7-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="ee3c7-108">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ee3c7-108">For example:</span></span>

![Domyślna czcionka kontrolna w .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="ee3c7-110">Ta zmiana została wmazana w celu dostosowania do [wytycznych dotyczących środowiska użytkownika systemu Windows .](/windows/win32/uxguide/vis-fonts#fonts-and-colors)</span><span class="sxs-lookup"><span data-stu-id="ee3c7-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="ee3c7-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="ee3c7-111">Version introduced</span></span>

<span data-ttu-id="ee3c7-112">3.0</span><span class="sxs-lookup"><span data-stu-id="ee3c7-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="ee3c7-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="ee3c7-113">Recommended action</span></span>

<span data-ttu-id="ee3c7-114">Ze względu na zmianę rozmiaru formularzy i formantów upewnij się, że aplikacja renderuje poprawnie.</span><span class="sxs-lookup"><span data-stu-id="ee3c7-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="ee3c7-115">Aby zachować oryginalną czcionkę, ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="ee3c7-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="ee3c7-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="ee3c7-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="ee3c7-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="ee3c7-117">Category</span></span>

- <span data-ttu-id="ee3c7-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ee3c7-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="ee3c7-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="ee3c7-119">Affected APIs</span></span>

<span data-ttu-id="ee3c7-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="ee3c7-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
