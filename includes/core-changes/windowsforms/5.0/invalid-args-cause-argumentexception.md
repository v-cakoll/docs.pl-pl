---
ms.openlocfilehash: f1fc70075ef09a4f036c69788342c07ee51d72ce
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83702473"
---
### <a name="winforms-methods-now-throw-argumentexception"></a>Metody WinForms teraz generują ArgumentException

Niektóre metody Windows Forms teraz generują <xref:System.ArgumentException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.

#### <a name="change-description"></a>Zmień opis

Wcześniej przekazywanie argumentów nieoczekiwanego lub nieprawidłowego typu do określonych metod Windows Forms spowoduje nieokreślony stan. Począwszy od platformy .NET 5,0, metody te generują teraz, <xref:System.ArgumentException> gdy przekazane nieprawidłowe argumenty.

Zgłaszanie jest <xref:System.ArgumentException> zgodne z zachowaniem środowiska uruchomieniowego .NET. Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.

Poniższa tabela zawiera listę odpowiednich metod i parametrów:

| Metoda | Nazwa parametru | Warunek | Dodana wersja |
|-|-|-|
| <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName> | `item` | Argument nie jest typu <xref:System.Windows.Forms.TabPage> . | 5,0 wersja zapoznawcza 1 |

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0 — wersja zapoznawcza 1

#### <a name="recommended-action"></a>Zalecana akcja

- Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.
- W razie potrzeby dojście do <xref:System.ArgumentException> wywołania metody.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:System.Windows.Forms.TabControl.GetToolTipText(System.Object)?displayProperty=fullName>

<!-- 

#### Affected APIs

- `M:System.Windows.Forms.TabControl.GetToolTipText(System.Object)`

-->
