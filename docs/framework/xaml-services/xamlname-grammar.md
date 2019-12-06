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
ms.openlocfilehash: a1e7a5a03db4a24ed4d13d62899754cfe9e76b56
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837158"
---
# <a name="xamlname-grammar"></a>XamlName — Gramatyka
Gramatyka XAML to określona Gramatyka zdefiniowana w specyfikacji języka XAML [MS-XAML], która jest odtwarzana w tym miejscu dla wygody.  
  
## <a name="from-the-xaml-specification"></a>Ze specyfikacji języka XAML  
 Specyfikacja [MS-XAML] definiuje gramatykę XamlName do identyfikowania zestawu dozwolonych identyfikatorów symbolicznych używanych dla typów i właściwości.  
  
 Wartości ciągu typu XamlName muszą być zgodne z następującą gramatyką:  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Który przyjmuje następujące ogólne wartości kategorii, zgodnie z definicją w bazie danych znaków Unicode  

| Kategoria Unicode   | Opis                   |
|--------------------|-------------------------------|
| Lu                 | Litera, Wielkie litery             |
| Ll                 | Litera, Małe litery             |
| Lt                 | Litera, Duże litery na początku wyrazu             |
| Lm                 | Litera, Modyfikator              |
| Lo                 | Litera, Inne                 |
| Mn                 | Oznacz, bez odstępów             |
| MC                 | Znak, Odstępy mieszane       |
| Nd                 | Liczba, dziesiętna               |
| NL                 | Liczba, Litera                |
 
 XAML definiuje drugą gramatykę, DottedXamlName, która jest używana do zakwalifikowanych odwołań do właściwości i zdarzeń, a także dla dołączonych elementów członkowskich. Aby uzyskać więcej informacji, zobacz Omówienie <xref:System.Windows.DependencyProperty> i [XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).  
  
 Wartości ciągu typu DottedXamlName muszą być zgodne z następującą gramatyką:  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać pełną specyfikację, zobacz [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).
