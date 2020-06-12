---
ms.openlocfilehash: f42da00487735acdcc60f876c75e1dfd17103008
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/11/2020
ms.locfileid: "84702451"
---
### <a name="winforms-properties-now-throw-argumentoutofrangeexception"></a>Właściwości WinForms teraz generują wyjątku ArgumentOutOfRangeException

Niektóre właściwości Windows Forms teraz zwracają <xref:System.ArgumentOutOfRangeException> dla nieprawidłowych argumentów, w których wcześniej nie zostały.

#### <a name="change-description"></a>Zmień opis

Wcześniej te właściwości spowodowały różne wyjątki, takie jak <xref:System.NullReferenceException> , <xref:System.IndexOutOfRangeException> , lub <xref:System.ArgumentException> , gdy przekazane są argumenty poza zakresem. Począwszy od platformy .NET 5,0, te właściwości generują teraz, <xref:System.ArgumentOutOfRangeException> gdy przekazane argumenty są poza zakresem.

Zgłaszanie jest <xref:System.ArgumentOutOfRangeException> zgodne z zachowaniem środowiska uruchomieniowego .NET. Usprawnia to również środowisko debugowania, przez co jasno komunikuje się, który argument jest nieprawidłowy.

#### <a name="version-introduced"></a>Wprowadzona wersja

.NET 5,0

#### <a name="recommended-action"></a>Zalecana akcja

- Zaktualizuj kod, aby zapobiec przekazywaniu nieprawidłowych argumentów.
- Jeśli to konieczne, należy obsłużyć <xref:System.ArgumentOutOfRangeException> podczas ustawiania właściwości.

#### <a name="category"></a>Kategoria

Windows Forms

#### <a name="affected-apis"></a>Dotyczy interfejsów API

W poniższej tabeli wymieniono odpowiednie właściwości i parametry:

> [!div class="mx-tdBreakAll"]
> | Właściwość | Nazwa parametru | Dodana wersja |
> |-|-|-|
> | <xref:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)?displayProperty=nameWithType> | `index` | 5,0 wersja zapoznawcza 5 |
> | <xref:System.Windows.Forms.TreeNode.ImageIndex?displayProperty=nameWithType> | `value` | 5,0 wersja zapoznawcza 6 |
> | <xref:System.Windows.Forms.TreeNode.SelectedImageIndex?displayProperty=nameWithType> | `value` | 5,0 wersja zapoznawcza 6 |

<!-- 

#### Affected APIs

- `P:System.Windows.Forms.ListBox.IntegerCollection.Item(System.Int32)`
- `P:System.Windows.Forms.TreeNode.ImageIndex`
- `P:System.Windows.Forms.TreeNode.SelectedImageIndex`

-->
