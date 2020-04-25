---
ms.openlocfilehash: 5212c5d9513a8ef5f51693857d0ddb60db4e49b9
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158407"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teraz generują ArgumentException

Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.

#### <a name="change-description"></a>Zmień opis

Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan. Począwszy od platformy .NET 5,0, metody te generują <xref:System.ArgumentException> teraz, gdy przekazane nieprawidłowe argumenty.

Zgłaszanie <xref:System.ArgumentException> jest zgodne z zachowaniem środowiska uruchomieniowego .NET. Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.

Poniższa tabela zawiera listę odpowiednich metod i parametrów:

| Metoda | Nazwa parametru | Warunek | Dodana wersja |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument nie jest typu <xref:System.Windows.Forms.TabPage>. | 5,0 wersja zapoznawcza 1 |

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0 — wersja zapoznawcza 1

#### <a name="recommended-action"></a>Zalecana akcja

- Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.
- W razie potrzeby dojście <xref:System.ArgumentException> do wywołania metody.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
