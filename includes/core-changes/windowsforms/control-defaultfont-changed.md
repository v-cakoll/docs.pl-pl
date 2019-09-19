---
ms.openlocfilehash: 02dbf5ccca97f5e7d2e1fada39bdf601cf37906f
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/19/2019
ms.locfileid: "71119360"
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