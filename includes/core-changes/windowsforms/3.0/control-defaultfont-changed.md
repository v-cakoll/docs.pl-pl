---
ms.openlocfilehash: b0c4e9617677cf95e3a059b57f3d50ddfb072f4a
ms.sourcegitcommit: 7e2128d4a4c45b4274bea3b8e5760d4694569ca1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/14/2020
ms.locfileid: "75936996"
---
### <a name="default-control-font-changed-to-segoe-ui-9-pt"></a>Domyślna czcionka kontrolki zmieniono na Segoe UI 9 pt

#### <a name="change-description"></a>Opis zmiany

W .NET Framework Właściwość <xref:System.Windows.Forms.Control.DefaultFont?displayProperty=nameWithType> została ustawiona na `Microsoft Sans Serif 8 pt`. Na poniższej ilustracji przedstawiono okno, które używa czcionki domyślnej.

![Domyślna czcionka kontrolki w .NET Framework](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-framework.png)

Począwszy od platformy .NET Core 3,0, domyślna czcionka jest ustawiona na `Segoe UI 9 pt` (taka sama czcionka jak <xref:System.Drawing.SystemFonts.MessageBoxFont?displayProperty=nameWithType>). W wyniku tej zmiany rozmiar formularzy i kontrolek ma rozmiar o 27% większy do konta w celu uzyskania większego rozmiaru nowej czcionki domyślnej. Na przykład:

![Domyślna czcionka kontrolna w programie .NET Core](~/docs/images/core-changes/windowsforms/control-defaultfont-changed/defaultfont-core.png)

Ta zmiana została wprowadzona w celu dostosowania ze [wskazówkami dotyczącymi środowiska użytkownika systemu Windows](/windows/win32/uxguide/vis-fonts#fonts-and-colors).

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecane działanie

Ze względu na zmianę rozmiaru formularzy i kontrolek upewnij się, że aplikacja jest renderowana poprawnie.

Aby zachować oryginalną czcionkę, ustaw czcionkę domyślną formularza na `Microsoft Sans Serif 8 pt`. Na przykład:

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
