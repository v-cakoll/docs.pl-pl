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
ms.openlocfilehash: 32fd7b7b952ebbc853e41c0a8276d1ab487e619f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xamlname-grammar"></a>XamlName — Gramatyka
Xamlname — gramatyka jest określonych gramatyki, która jest zdefiniowana w specyfikacji języka XAML [MS-XAML], który jest podany tutaj dla wygody.  
  
## <a name="from-the-xaml-specification"></a>W specyfikacji języka XAML  
 Specification [MS-XAML] określa gramatyki xamlname — do identyfikowania zestawów prawne symboliczne identyfikatory używane dla typów i właściwości.  
  
 Ciąg typu, który musi odpowiadać xamlname — gramatyka następujące wartości:  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 Dział następujące wartości ogólne kategorii zgodnie z definicją w bazie danych znak Unicode  
  
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
  
 XAML definiuje drugi gramatyki, dottedxamlname —, która jest używana dla właściwości i zdarzenia kwalifikowanego odwołania, a także dla dołączone elementy członkowskie. Aby uzyskać więcej informacji, zobacz <xref:System.Windows.DependencyProperty> i [omówienie XAML (WPF)](../../../docs/framework/wpf/advanced/xaml-overview-wpf.md).  
  
 Ciąg wartości, które są dottedxamlname — musi odpowiadać gramatyce następującego typu:  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a>Uwagi  
 Pełne specyfikacji, zobacz [ \[MS XAML\]](http://go.microsoft.com/fwlink/?LinkId=114525).
