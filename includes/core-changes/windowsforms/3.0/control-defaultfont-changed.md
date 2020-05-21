---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721413"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a><span data-ttu-id="cf162-101">Domyślna czcionka kontrolki zmieniono na Segoe UI 9 pt</span><span class="sxs-lookup"><span data-stu-id="cf162-101">Default control font changed to Segoe UI 9 pt</span></span>

#### <a name="change-description"></a><span data-ttu-id="cf162-102">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="cf162-102">Change description</span></span>

<span data-ttu-id="cf162-103">W .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> Właściwość została ustawiona na `Microsoft Sans Serif 8 pt` .</span><span class="sxs-lookup"><span data-stu-id="cf162-103">In .NET Framework, the <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> property was set to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="cf162-104">Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="cf162-104">The following image shows a window that uses the default font.</span></span>

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

<span data-ttu-id="cf162-106">Począwszy od platformy .NET Core 3,0, domyślna czcionka jest ustawiana na `Segoe UI 9 pt` (taką samą czcionkę jak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ).</span><span class="sxs-lookup"><span data-stu-id="cf162-106">Starting in .NET Core 3.0, the default font is set to `Segoe UI 9 pt` (the same font as <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>).</span></span> <span data-ttu-id="cf162-107">W wyniku tej zmiany rozmiar formularzy i kontrolek ma rozmiar o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej.</span><span class="sxs-lookup"><span data-stu-id="cf162-107">As a result of this change, forms and controls are sized about 27% larger to account for the larger size of the new default font.</span></span> <span data-ttu-id="cf162-108">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cf162-108">For example:</span></span>

![Domyślna czcionka kontrolna w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

<span data-ttu-id="cf162-110">Ta zmiana została wprowadzona w celu dostosowania ze [wskazówkami dotyczącymi środowiska użytkownika systemu Windows](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span><span class="sxs-lookup"><span data-stu-id="cf162-110">This change was made to align with [Windows user experience (UX) guidelines](/windows/win32/uxguide/vis-fonts#fonts-and-colors).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="cf162-111">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="cf162-111">Version introduced</span></span>

<span data-ttu-id="cf162-112">3.0</span><span class="sxs-lookup"><span data-stu-id="cf162-112">3.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="cf162-113">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="cf162-113">Recommended action</span></span>

<span data-ttu-id="cf162-114">Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.</span><span class="sxs-lookup"><span data-stu-id="cf162-114">Because of the change in the size of forms and controls, ensure that your application renders correctly.</span></span>

<span data-ttu-id="cf162-115">Aby zachować oryginalną czcionkę, Ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8 pt` .</span><span class="sxs-lookup"><span data-stu-id="cf162-115">To retain the original font, set your form's default font to `Microsoft Sans Serif 8 pt`.</span></span> <span data-ttu-id="cf162-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="cf162-116">For example:</span></span>

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a><span data-ttu-id="cf162-117">Kategoria</span><span class="sxs-lookup"><span data-stu-id="cf162-117">Category</span></span>

- <span data-ttu-id="cf162-118">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cf162-118">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="cf162-119">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="cf162-119">Affected APIs</span></span>

<span data-ttu-id="cf162-120">Brak.</span><span class="sxs-lookup"><span data-stu-id="cf162-120">None.</span></span>

<!--

#### Affected APIs

- Not detectable via API analysis

-->
