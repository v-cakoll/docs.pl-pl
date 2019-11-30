---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/28/2019
ms.locfileid: "74643950"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont` zmienić na `Segoe UI 9pt`

#### <a name="change-description"></a>Zmień opis

W .NET Framework Właściwość <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> została ustawiona na `Microsoft Sans Serif 8pt`. Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

W programie .NET Core rozpoczynającym się od platformy .NET Core 3,0 jest ustawiony na `Segoe UI 9pt` (tę samą czcionkę co <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). W wyniku tej zmiany rozmiar formularzy i kontrolek zostanie powiększony o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej. Na przykład:

![Domyślna czcionka kontrolek — w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Ta zmiana została wprowadzona w celu dostosowania się do [wskazówek dotyczących środowiska użytkownika systemu Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.

Aby zachować oryginalną czcionkę, ustaw czcionkę domyślną formularza na `Microsoft Sans Serif 8pt`. Na przykład:

```csharp
public MyForm()
{
    InitializeComponent();
    Font = new Font(new FontFamily("Microsoft Sans Serif"), 8f);
}
```

#### <a name="category"></a>Kategoria

- Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak.

<!--

### Affected APIs

- Not detectable via API analysis

-->
