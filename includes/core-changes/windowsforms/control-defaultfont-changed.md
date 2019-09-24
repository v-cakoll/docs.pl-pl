---
ms.openlocfilehash: 843007ac6467584fbe6350b6ea19ef67609d73e2
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217032"
---
### <a name="controldefaultfont-changed-to-segoe-ui-9pt"></a>`Control.DefaultFont`zmieniono na`Segoe UI 9pt`

#### <a name="change-description"></a>Zmień opis

W .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> właściwość została ustawiona na `Microsoft Sans Serif 8pt`. Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

W programie .NET Core rozpoczynającym się od platformy .NET Core 3,0 jest `Segoe UI 9pt` ona ustawiona na wartość ( <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>taka sama czcionka jak). W wyniku tej zmiany rozmiar formularzy i kontrolek zostanie powiększony o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej. Na przykład:

![Domyślna czcionka kontrolek — w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Ta zmiana została wprowadzona w celu dostosowania się do [wskazówek dotyczących środowiska użytkownika systemu Windows](https://docs.microsoft.com/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.

Aby zachować oryginalną czcionkę, Ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8pt`. Na przykład:

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
