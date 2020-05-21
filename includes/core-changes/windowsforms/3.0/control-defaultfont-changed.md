---
ms.openlocfilehash: 0b2d3c1383246d4259c6d906ecf9dab927f4bdb1
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83721413"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Domyślna czcionka kontrolki zmieniono na Segoe UI 9 pt

#### <a name="change-description"></a>Zmień opis

W .NET Framework <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> Właściwość została ustawiona na `Microsoft Sans Serif 8 pt` . Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Począwszy od platformy .NET Core 3,0, domyślna czcionka jest ustawiana na `Segoe UI 9 pt` (taką samą czcionkę jak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType> ). W wyniku tej zmiany rozmiar formularzy i kontrolek ma rozmiar o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej. Przykład:

![Domyślna czcionka kontrolna w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Ta zmiana została wprowadzona w celu dostosowania ze [wskazówkami dotyczącymi środowiska użytkownika systemu Windows](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.

Aby zachować oryginalną czcionkę, Ustaw domyślną czcionkę formularza na `Microsoft Sans Serif 8 pt` . Przykład:

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

#### Affected APIs

- Not detectable via API analysis

-->
