---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119360"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a><span data-ttu-id="de1e6-101">`Control.DefaultFont`zmieniono na`Segoe UI 9pt`</span><span class="sxs-lookup"><span data-stu-id="de1e6-101">`Control.DefaultFont` changed to `Segoe UI 9pt`</span></span> 

#### <a name="change-description"></a><span data-ttu-id="de1e6-102">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="de1e6-102">Change description</span></span>

<span data-ttu-id="de1e6-103">W .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> właściwość została ustawiona na `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="de1e6-103">In the .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="de1e6-104">Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="de1e6-104">The following figure shows a window that uses the default font.</span></span>

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="de1e6-106">W programie .NET Core rozpoczynającym się od platformy .NET Core 3,0 jest `Segoe UI 9pt` ona ustawiona na wartość ( <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>taka sama czcionka jak).</span><span class="sxs-lookup"><span data-stu-id="de1e6-106">In .NET Core starting with .NET Core 3.0, it is set to `Segoe UI 9pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="de1e6-107">W wyniku tej zmiany rozmiar formularzy i kontrolek zostanie powiększony o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="de1e6-107">As a result of this change, forms and controls will be sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="de1e6-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="de1e6-108">For example:</span></span>

![Domyślna czcionka kontrolek — w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="de1e6-110">Ta zmiana została wprowadzona w celu dostosowania się do [wskazówek dotyczących środowiska użytkownika systemu Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="de1e6-110">This change was made to align with [Windows UX guidelines](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="de1e6-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="de1e6-111">Version introduced</span></span>

<span data-ttu-id="de1e6-112">3.0</span><span class="sxs-lookup"><span data-stu-id="de1e6-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="de1e6-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="de1e6-113">Recommended action</span></span>

<span data-ttu-id="de1e6-114">Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="de1e6-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="de1e6-115">Aby zachować oryginalną czcionkę, Ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8pt`.</span><span class="sxs-lookup"><span data-stu-id="de1e6-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8pt`.</span></span> <span data-ttu-id="de1e6-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="de1e6-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="de1e6-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="de1e6-117">Category</span></span>

- <span data-ttu-id="de1e6-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="de1e6-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="de1e6-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="de1e6-119">Affected APIs</span></span>

<span data-ttu-id="de1e6-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="de1e6-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->