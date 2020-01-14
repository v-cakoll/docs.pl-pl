---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936996"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="1e412-101">Domyślna czcionka kontrolki zmieniono na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="1e412-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="1e412-102">Opis zmiany</span><span class="sxs-lookup"><span data-stu-id="1e412-102">Change description</span></span>

<span data-ttu-id="1e412-103">W .NET Framework Właściwość <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> została ustawiona na `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="1e412-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="1e412-104">Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="1e412-104">The following image shows a window that uses the default font.</span></span>

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="1e412-106">Począwszy od platformy .NET Core 3,0, domyślna czcionka jest ustawiona na `Segoe UI 9 pt` (taka sama czcionka jak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span><span class="sxs-lookup"><span data-stu-id="1e412-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="1e412-107">W wyniku tej zmiany rozmiar formularzy i kontrolek ma rozmiar o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="1e412-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="1e412-108">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e412-108">For example:</span></span>

![Domyślna czcionka kontrolna w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="1e412-110">Ta zmiana została wprowadzona w celu dostosowania ze [wskazówkami dotyczącymi środowiska użytkownika systemu Windows](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="1e412-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="1e412-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="1e412-111">Version introduced</span></span>

<span data-ttu-id="1e412-112">3.0</span><span class="sxs-lookup"><span data-stu-id="1e412-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="1e412-113">Zalecane działanie</span><span class="sxs-lookup"><span data-stu-id="1e412-113">Recommended action</span></span>

<span data-ttu-id="1e412-114">Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="1e412-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="1e412-115">Aby zachować oryginalną czcionkę, ustaw czcionkę domyślną formularza na `Microsoft Sans Serif 8 pt`.</span><span class="sxs-lookup"><span data-stu-id="1e412-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="1e412-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1e412-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="1e412-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="1e412-117">Category</span></span>

- <span data-ttu-id="1e412-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1e412-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="1e412-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="1e412-119">Affected APIs</span></span>

<span data-ttu-id="1e412-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="1e412-120">None.</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
