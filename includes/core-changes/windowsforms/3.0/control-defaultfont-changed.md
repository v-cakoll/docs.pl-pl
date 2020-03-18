---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75936996"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Domyślna czcionka kontrolna zmieniona na Segoe UI 9 pkt

#### <a name="change-description"></a>Zmień opis

W platformie <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> .NET Framework `Microsoft Sans Serif 8 pt`właściwość została ustawiona na . Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.

![Domyślna czcionka kontrolna w programach .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Począwszy od .NET Core 3.0, `Segoe UI 9 pt` domyślna czcionka <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>jest ustawiona na (ta sama czcionka co ). W wyniku tej zmiany formularze i formanty są o 27% większe, aby uwzględnić większy rozmiar nowej czcionki domyślnej. Przykład:

![Domyślna czcionka kontrolna w .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Ta zmiana została wmazana w celu dostosowania do [wytycznych dotyczących środowiska użytkownika systemu Windows .](/windows/win32/uxguide/vis-fonts#fonts-and-colors)

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ze względu na zmianę rozmiaru formularzy i formantów upewnij się, że aplikacja renderuje poprawnie.

Aby zachować oryginalną czcionkę, ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8 pt`. Przykład:

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
