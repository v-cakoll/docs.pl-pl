---
title: XamlName — Gramatyka
ms.date: 03/30/2017
helpviewer_keywords:
- DottedXamlName grammar [XAML Services]
- grammar [XAML Services], DottedXamlName
- grammar [XAML Services], XamlName
- names in XAML [XAML Services]
- XamlName grammar [XAML Services]
ms.assetid: 11e4cada-41d2-494d-9531-0d3df4dfcbe3
ms.openlocfilehash: 2fc74990b15caaa9b58e6eea5b0212ea22505674
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "82071830"
---
# <a name="xamlname-grammar"></a>XamlName — Gramatyka

XamlName Grammar jest określoną gramatyką zdefiniowaną w specyfikacji języka XAML [MS-XAML], która jest powielana tutaj dla wygody.

## <a name="from-the-xaml-specification"></a>Ze specyfikacji XAML

Specyfikacja [MS-XAML] definiuje gramatyki XamlName do identyfikacji zestawu prawnych identyfikatorów symbolicznych używanych dla typów i właściwości.

Wartości ciągów typu XamlName muszą być zgodne z następującą gramatyką:

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

Który zakłada następujące ogólne wartości kategorii zdefiniowane w bazie danych znaków Unicode

| Kategoria Unicode   | Opis                   |
|--------------------|-------------------------------|
| Lu                 | Litera, Wielkie litery             |
| Ll                 | Litera, Małe litery             |
| Lt                 | Litera, Duże litery na początku wyrazu             |
| Lm                 | Litera, Modyfikator              |
| Lo                 | Litera, Inne                 |
| Mn                 | Oznacz, Bez odstępów             |
| Mc                 | Znak, Odstępy mieszane       |
| Nd                 | Liczba, dziesiętna               |
| Nl                 | Liczba, Litera                |

XAML definiuje drugą gramatykę, DottedXamlName, która jest używana dla odwołań do właściwości i zdarzeń kwalifikowanych, a także dla dołączonych elementów członkowskich. Aby uzyskać więcej <xref:System.Windows.DependencyProperty> informacji, zobacz i [Omówienie XAML (WPF)](../fundamentals/xaml.md).

Wartości ciągów typu DottedXamlName muszą być zgodne z następującą gramatyką:

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a>Uwagi

Aby uzyskać pełną specyfikację, zobacz [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
