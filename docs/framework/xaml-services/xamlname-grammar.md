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
ms.openlocfilehash: 642ca16142bdfe78a40ddf4e6a3a79ce6a8a4985
ms.sourcegitcommit: 5c1abeec15fbddcc7dbaa729fabc1f1f29f12045
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2019
ms.locfileid: "58031605"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="14adf-102">XamlName — Gramatyka</span><span class="sxs-lookup"><span data-stu-id="14adf-102">XamlName Grammar</span></span>
<span data-ttu-id="14adf-103">Xamlname — gramatyka jest określone gramatyki, która jest zdefiniowana w specyfikacji języka XAML [MS-XAML], który jest przedstawiony tutaj dla wygody.</span><span class="sxs-lookup"><span data-stu-id="14adf-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="14adf-104">Ze specyfikacji XAML</span><span class="sxs-lookup"><span data-stu-id="14adf-104">From the XAML Specification</span></span>  
 <span data-ttu-id="14adf-105">Specification [MS-XAML] określa gramatyki XamlName do identyfikowania zestawów prawne identyfikatory symboliczne używane dla typów i właściwości.</span><span class="sxs-lookup"><span data-stu-id="14adf-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="14adf-106">Wartości ciągów, które są typu, który XamlName musi odpowiadać poniżej gramatyką:</span><span class="sxs-lookup"><span data-stu-id="14adf-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="14adf-107">Który założono następujące wartości kategorii Ogólne, zgodnie z definicją w bazie danych znaków Unicode</span><span class="sxs-lookup"><span data-stu-id="14adf-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  
  
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
  
 <span data-ttu-id="14adf-108">XAML definiuje drugi gramatykę, dottedxamlname —, który jest używany dla właściwości i zdarzeń kwalifikowane odwołania oraz dla dołączone elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="14adf-108">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="14adf-109">Aby uzyskać więcej informacji, zobacz <xref:System.Windows.DependencyProperty> i [Przegląd XAML (WPF)](../wpf/advanced/xaml-overview-wpf.md).</span><span class="sxs-lookup"><span data-stu-id="14adf-109">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../wpf/advanced/xaml-overview-wpf.md).</span></span>  
  
 <span data-ttu-id="14adf-110">Wartości ciągów, które są typu, które muszą spełniać dottedxamlname — gramatyka następujące:</span><span class="sxs-lookup"><span data-stu-id="14adf-110">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="14adf-111">Uwagi</span><span class="sxs-lookup"><span data-stu-id="14adf-111">Remarks</span></span>  
 <span data-ttu-id="14adf-112">Aby uzyskać pełną specyfikację zobacz [ \[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="14adf-112">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
