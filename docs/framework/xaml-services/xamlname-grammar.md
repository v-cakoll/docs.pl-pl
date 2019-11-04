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
ms.openlocfilehash: a39d25f03583ab9020878b7a659bc99489231ff9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458885"
---
# <a name="xamlname-grammar"></a><span data-ttu-id="13a13-102">XamlName — Gramatyka</span><span class="sxs-lookup"><span data-stu-id="13a13-102">XamlName Grammar</span></span>
<span data-ttu-id="13a13-103">Gramatyka XAML to określona Gramatyka zdefiniowana w specyfikacji języka XAML [MS-XAML], która jest odtwarzana w tym miejscu dla wygody.</span><span class="sxs-lookup"><span data-stu-id="13a13-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>  
  
## <a name="from-the-xaml-specification"></a><span data-ttu-id="13a13-104">Ze specyfikacji języka XAML</span><span class="sxs-lookup"><span data-stu-id="13a13-104">From the XAML Specification</span></span>  
 <span data-ttu-id="13a13-105">Specyfikacja [MS-XAML] definiuje gramatykę XamlName do identyfikowania zestawu dozwolonych identyfikatorów symbolicznych używanych dla typów i właściwości.</span><span class="sxs-lookup"><span data-stu-id="13a13-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>  
  
 <span data-ttu-id="13a13-106">Wartości ciągu typu XamlName muszą być zgodne z następującą gramatyką:</span><span class="sxs-lookup"><span data-stu-id="13a13-106">String values that are of type XamlName must conform to the following grammar:</span></span>  
  
```xaml  
XamlName ::= NameStartChar ( NameChar )*   
NameStartChar ::= LetterCharacter | '_'   
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter   
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl   
DecimalDigit ::= UnicodeNd   
CombiningCharacter ::= UnicodeMn | UnicodeMc  
```  
  
 <span data-ttu-id="13a13-107">Który przyjmuje następujące ogólne wartości kategorii, zgodnie z definicją w bazie danych znaków Unicode</span><span class="sxs-lookup"><span data-stu-id="13a13-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>  

| <span data-ttu-id="13a13-108">Kategoria Unicode</span><span class="sxs-lookup"><span data-stu-id="13a13-108">Unicode category</span></span>   | <span data-ttu-id="13a13-109">Opis</span><span class="sxs-lookup"><span data-stu-id="13a13-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="13a13-110">Lu</span><span class="sxs-lookup"><span data-stu-id="13a13-110">Lu</span></span>                 | <span data-ttu-id="13a13-111">Litera, Wielkie litery</span><span class="sxs-lookup"><span data-stu-id="13a13-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="13a13-112">Ll</span><span class="sxs-lookup"><span data-stu-id="13a13-112">Ll</span></span>                 | <span data-ttu-id="13a13-113">Litera, Małe litery</span><span class="sxs-lookup"><span data-stu-id="13a13-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="13a13-114">Lt</span><span class="sxs-lookup"><span data-stu-id="13a13-114">Lt</span></span>                 | <span data-ttu-id="13a13-115">Litera, Duże litery na początku wyrazu</span><span class="sxs-lookup"><span data-stu-id="13a13-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="13a13-116">Lm</span><span class="sxs-lookup"><span data-stu-id="13a13-116">Lm</span></span>                 | <span data-ttu-id="13a13-117">Litera, Modyfikator</span><span class="sxs-lookup"><span data-stu-id="13a13-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="13a13-118">Lo</span><span class="sxs-lookup"><span data-stu-id="13a13-118">Lo</span></span>                 | <span data-ttu-id="13a13-119">Litera, Inne</span><span class="sxs-lookup"><span data-stu-id="13a13-119">Letter, Other</span></span>                 |
| <span data-ttu-id="13a13-120">Mn</span><span class="sxs-lookup"><span data-stu-id="13a13-120">Mn</span></span>                 | <span data-ttu-id="13a13-121">Oznacz, bez odstępów</span><span class="sxs-lookup"><span data-stu-id="13a13-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="13a13-122">MC</span><span class="sxs-lookup"><span data-stu-id="13a13-122">Mc</span></span>                 | <span data-ttu-id="13a13-123">Znak, Odstępy mieszane</span><span class="sxs-lookup"><span data-stu-id="13a13-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="13a13-124">Nd</span><span class="sxs-lookup"><span data-stu-id="13a13-124">Nd</span></span>                 | <span data-ttu-id="13a13-125">Liczba, dziesiętna</span><span class="sxs-lookup"><span data-stu-id="13a13-125">Number, Decimal</span></span>               |
| <span data-ttu-id="13a13-126">NL</span><span class="sxs-lookup"><span data-stu-id="13a13-126">Nl</span></span>                 | <span data-ttu-id="13a13-127">Liczba, Litera</span><span class="sxs-lookup"><span data-stu-id="13a13-127">Number, Letter</span></span>                |
 
 <span data-ttu-id="13a13-128">XAML definiuje drugą gramatykę, DottedXamlName, która jest używana do zakwalifikowanych odwołań do właściwości i zdarzeń, a także dla dołączonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="13a13-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="13a13-129">Aby uzyskać więcej informacji, zobacz Omówienie <xref:System.Windows.DependencyProperty> i [XAML (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="13a13-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../../desktop-wpf/fundamentals/xaml.md).</span></span>  
  
 <span data-ttu-id="13a13-130">Wartości ciągu typu DottedXamlName muszą być zgodne z następującą gramatyką:</span><span class="sxs-lookup"><span data-stu-id="13a13-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>  
  
```xaml  
DottedXamlName ::= XamlName '.' XamlName  
```  
  
## <a name="remarks"></a><span data-ttu-id="13a13-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="13a13-131">Remarks</span></span>  
 <span data-ttu-id="13a13-132">Aby uzyskać pełną specyfikację, zobacz [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span><span class="sxs-lookup"><span data-stu-id="13a13-132">For the complete specification, see [\[MS-XAML\]](https://go.microsoft.com/fwlink/?LinkId=114525).</span></span>
