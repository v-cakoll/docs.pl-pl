---
ms.openlocfilehash: d1562cb76f37b6cc2aeb6fe2f7c17c393e169e84
ms.sourcegitcommit: c2c1269a81ffdcfc8675bcd9a8505b1a11ffb271
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/25/2020
ms.locfileid: "82158485"
---
### <a name="invalidasynchronousstateexception-moved-to-another-assembly"></a>InvalidAsynchronousStateException — przeniesiony do innego zestawu

<xref:System.ComponentModel.InvalidAsynchronousStateException> Klasa została przeniesiona.

#### <a name="change-description"></a>Zmień opis

W programie .NET Core 2,2 i starszych wersjach <xref:System.ComponentModel.InvalidAsynchronousStateException> Klasa jest dostępna w zestawie *System. ComponentModel. TypeConverter* .

Począwszy od platformy .NET Core 3,0, znajduje się on w zestawie *System. ComponentModel. prymityws* .

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana dotyczy tylko aplikacji, które używają odbicia do <xref:System.ComponentModel.InvalidAsynchronousStateException> ładowania przez wywołanie metody, takiej <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> jak lub przeciążenia <xref:System.Activator.CreateInstance%2A?displayProperty=nameWithType> , która zakłada, że typ znajduje się w określonym zestawie. W takim przypadku należy zaktualizować zestaw przywoływany w wywołaniu metody, aby odzwierciedlić nową lokalizację zestawu.

#### <a name="category"></a>Kategoria

Podstawowe biblioteki platformy .NET

#### <a name="affected-apis"></a>Dotyczy interfejsów API

Brak.

<!--

### Affected APIs

- Not detectable via API analysis

-->
