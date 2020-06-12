---
ms.openlocfilehash: aab7d8538c875e35c832acc2a6c64beb84d4fb47
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702450"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teraz generują ArgumentException

Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.

#### <a name="change-description"></a>Zmień opis

Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan. Począwszy od platformy .NET 5,0, metody te generują teraz, <xref:System.ArgumentException> gdy przekazane nieprawidłowe argumenty.

Zgłaszanie jest <xref:System.ArgumentException> zgodne z zachowaniem środowiska uruchomieniowego .NET. Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.

Poniższa tabela zawiera listę odpowiednich metod i parametrów:

| Metoda | Nazwa parametru | Warunek | Dodana wersja |
|-|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument nie jest typu <xref:System.Windows.Forms.TabPage> . | 5,0 wersja zapoznawcza 1 |
| <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName> | `format` | Argument to `null` , <xref:System.String.Empty?displayProperty=nameWithType> lub biały znak. | 5,0 wersja zapoznawcza 5 |

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0

#### <a name="recommended-action"></a>Zalecana akcja

- Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.
- W razie potrzeby dojście do <xref:System.ArgumentException> wywołania metody.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>
- <xref:System.Windows.Forms.DataFormats.GetFormat(System.String)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`
- `M:System.Windows.Forms.DataFormats.GetFormat(System.String)`

-->
