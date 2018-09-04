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
ms.openlocfilehash: 2a934316517047da6b6aec8e88026024b9a25f65
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43514804"
---
# <a name="xamlname-grammar"></a>XamlName — Gramatyka
Xamlname — gramatyka jest określone gramatyki, która jest zdefiniowana w specyfikacji języka XAML [MS-XAML], który jest przedstawiony tutaj dla wygody.  
  
## <a name="from-the-xaml-specification"></a>Ze specyfikacji XAML  
 Specification [MS-XAML] określa gramatyki XamlName do identyfikowania zestawów prawne identyfikatory symboliczne używane dla typów i właściwości.  
  
 Wartości ciągów, które są typu, który XamlName musi odpowiadać poniżej gramatyką:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Który założono następujące wartości kategorii Ogólne, zgodnie z definicją w bazie danych znaków Unicode  
  
```  
Lu  
Letter, Uppercase  
Ll  
Letter, Lowercase  
Lt  
Letter, Titlecase  
Lm  
Letter, Modifier  
Lo  
Letter, Other  
Mn  
Mark, Non-Spacing  
Mc  
Mark, Spacing Combining  
Nd  
Number, Decimal  
Nl  
Number, Letter  
```  
  
 XAML definiuje drugi gramatykę, dottedxamlname —, który jest używany dla właściwości i zdarzeń kwalifikowane odwołania oraz dla dołączone elementy członkowskie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.DependencyProperty> i [Przegląd XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Wartości ciągów, które są typu, które muszą spełniać dottedxamlname — gramatyka następujące:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Uwagi  
 Aby uzyskać pełną specyfikację zobacz [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).
