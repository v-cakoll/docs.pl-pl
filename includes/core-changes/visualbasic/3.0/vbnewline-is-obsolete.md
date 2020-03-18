---
ms.openlocfilehash: 95a4c807f5c1077cf52f54b196e904ebc98c32f8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76116367"
---
### <a name="microsoftvisualbasicconstantsvbnewline-is-obsolete"></a>Microsoft.VisualBasic.Constants.vbNewLine jest przestarzały

Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> jest oznaczona jako [ \[przestarzała,\] ](xref:System.ObsoleteAttribute) zaczynając od wersji .NET Core 3.0 Preview 8.

#### <a name="version-introduced"></a>Wprowadzona wersja

3.0 Podgląd 8

#### <a name="change-description"></a>Zmień opis

Począwszy od .NET Core 3.0 Preview 8, [Atrybut](xref:System.ObsoleteAttribute) Przestarzałe <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName> został zastosowany do stałej. Użycie stałej tworzy ostrzeżenie kompilatora. W .NET Framework i poprzednich wersjach programu .NET Core nie został oznaczony jako przestarzały.

Ta zmiana została wmazana w celu obsługi języka Visual Basic jako języka dla tworzenia wielu platform. Stała <xref:Microsoft.VisualBasic.Constants.vbNewLine> jest odpowiednikiem `\r\n`sekwencji znaków nowej linii w systemie Windows. W systemach uniksowych nowy `\n`znak linii to .

#### <a name="recommended-action"></a>Zalecana akcja

Komunikat atrybutu [Przestarzałe](xref:System.ObsoleteAttribute) <xref:Microsoft.VisualBasic.Constants.vbNewLine> zawiera następujące zalecenie:

W przypadku powrotu karetki <xref:Microsoft.VisualBasic.Constants.vbCrLf>i wysuwu linii użyj . Aby uzyskać nową linię bieżącej <xref:System.Environment.NewLine?displayProperty=nameWithType>platformy, użyj .

#### <a name="category"></a>Kategoria

Visual Basic

#### <a name="affected-apis"></a>Dotyczy interfejsów API

- <xref:Microsoft.VisualBasic.Constants.vbNewLine?displayProperty=fullName>

<!--

### Affected APIs

- `F:Microsoft.VisualBasic.Constants.vbNewLine`

-->
