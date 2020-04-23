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
# <a name="xamlname-grammar"></a><span data-ttu-id="eb598-102">XamlName — Gramatyka</span><span class="sxs-lookup"><span data-stu-id="eb598-102">XamlName Grammar</span></span>

<span data-ttu-id="eb598-103">XamlName Grammar jest określoną gramatyką zdefiniowaną w specyfikacji języka XAML [MS-XAML], która jest powielana tutaj dla wygody.</span><span class="sxs-lookup"><span data-stu-id="eb598-103">XamlName Grammar is a specific grammar that is defined in the XAML language specification [MS-XAML], which is reproduced here for convenience.</span></span>

## <a name="from-the-xaml-specification"></a><span data-ttu-id="eb598-104">Ze specyfikacji XAML</span><span class="sxs-lookup"><span data-stu-id="eb598-104">From the XAML Specification</span></span>

<span data-ttu-id="eb598-105">Specyfikacja [MS-XAML] definiuje gramatyki XamlName do identyfikacji zestawu prawnych identyfikatorów symbolicznych używanych dla typów i właściwości.</span><span class="sxs-lookup"><span data-stu-id="eb598-105">The [MS-XAML] specification defines the grammar XamlName to identify the set of legal symbolic identifiers used for types and properties.</span></span>

<span data-ttu-id="eb598-106">Wartości ciągów typu XamlName muszą być zgodne z następującą gramatyką:</span><span class="sxs-lookup"><span data-stu-id="eb598-106">String values that are of type XamlName must conform to the following grammar:</span></span>

```xaml
XamlName ::= NameStartChar ( NameChar )*
NameStartChar ::= LetterCharacter | '_'
NameChar ::= NameStartChar | DecimalDigit | CombiningCharacter
LetterCharacter ::= UnicodeLu | UnicodeLl | UnicodeLo | UnicodeLt | UnicodeNl
DecimalDigit ::= UnicodeNd
CombiningCharacter ::= UnicodeMn | UnicodeMc
```

<span data-ttu-id="eb598-107">Który zakłada następujące ogólne wartości kategorii zdefiniowane w bazie danych znaków Unicode</span><span class="sxs-lookup"><span data-stu-id="eb598-107">Which assumes the following general category values as defined in the Unicode Character Database</span></span>

| <span data-ttu-id="eb598-108">Kategoria Unicode</span><span class="sxs-lookup"><span data-stu-id="eb598-108">Unicode category</span></span>   | <span data-ttu-id="eb598-109">Opis</span><span class="sxs-lookup"><span data-stu-id="eb598-109">Description</span></span>                   |
|--------------------|-------------------------------|
| <span data-ttu-id="eb598-110">Lu</span><span class="sxs-lookup"><span data-stu-id="eb598-110">Lu</span></span>                 | <span data-ttu-id="eb598-111">Litera, Wielkie litery</span><span class="sxs-lookup"><span data-stu-id="eb598-111">Letter, Uppercase</span></span>             |
| <span data-ttu-id="eb598-112">Ll</span><span class="sxs-lookup"><span data-stu-id="eb598-112">Ll</span></span>                 | <span data-ttu-id="eb598-113">Litera, Małe litery</span><span class="sxs-lookup"><span data-stu-id="eb598-113">Letter, Lowercase</span></span>             |
| <span data-ttu-id="eb598-114">Lt</span><span class="sxs-lookup"><span data-stu-id="eb598-114">Lt</span></span>                 | <span data-ttu-id="eb598-115">Litera, Duże litery na początku wyrazu</span><span class="sxs-lookup"><span data-stu-id="eb598-115">Letter, Titlecase</span></span>             |
| <span data-ttu-id="eb598-116">Lm</span><span class="sxs-lookup"><span data-stu-id="eb598-116">Lm</span></span>                 | <span data-ttu-id="eb598-117">Litera, Modyfikator</span><span class="sxs-lookup"><span data-stu-id="eb598-117">Letter, Modifier</span></span>              |
| <span data-ttu-id="eb598-118">Lo</span><span class="sxs-lookup"><span data-stu-id="eb598-118">Lo</span></span>                 | <span data-ttu-id="eb598-119">Litera, Inne</span><span class="sxs-lookup"><span data-stu-id="eb598-119">Letter, Other</span></span>                 |
| <span data-ttu-id="eb598-120">Mn</span><span class="sxs-lookup"><span data-stu-id="eb598-120">Mn</span></span>                 | <span data-ttu-id="eb598-121">Oznacz, Bez odstępów</span><span class="sxs-lookup"><span data-stu-id="eb598-121">Mark, Non-Spacing</span></span>             |
| <span data-ttu-id="eb598-122">Mc</span><span class="sxs-lookup"><span data-stu-id="eb598-122">Mc</span></span>                 | <span data-ttu-id="eb598-123">Znak, Odstępy mieszane</span><span class="sxs-lookup"><span data-stu-id="eb598-123">Mark, Spacing Combining</span></span>       |
| <span data-ttu-id="eb598-124">Nd</span><span class="sxs-lookup"><span data-stu-id="eb598-124">Nd</span></span>                 | <span data-ttu-id="eb598-125">Liczba, dziesiętna</span><span class="sxs-lookup"><span data-stu-id="eb598-125">Number, Decimal</span></span>               |
| <span data-ttu-id="eb598-126">Nl</span><span class="sxs-lookup"><span data-stu-id="eb598-126">Nl</span></span>                 | <span data-ttu-id="eb598-127">Liczba, Litera</span><span class="sxs-lookup"><span data-stu-id="eb598-127">Number, Letter</span></span>                |

<span data-ttu-id="eb598-128">XAML definiuje drugą gramatykę, DottedXamlName, która jest używana dla odwołań do właściwości i zdarzeń kwalifikowanych, a także dla dołączonych elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="eb598-128">XAML defines a second grammar, DottedXamlName, that is used for property and event qualified references, and also for attached members.</span></span> <span data-ttu-id="eb598-129">Aby uzyskać więcej <xref:System.Windows.DependencyProperty> informacji, zobacz i [Omówienie XAML (WPF)](../fundamentals/xaml.md).</span><span class="sxs-lookup"><span data-stu-id="eb598-129">For more information, see <xref:System.Windows.DependencyProperty> and [XAML Overview (WPF)](../fundamentals/xaml.md).</span></span>

<span data-ttu-id="eb598-130">Wartości ciągów typu DottedXamlName muszą być zgodne z następującą gramatyką:</span><span class="sxs-lookup"><span data-stu-id="eb598-130">String values that are of type DottedXamlName must conform to the following grammar:</span></span>

```xaml
DottedXamlName ::= XamlName '.' XamlName
```

## <a name="remarks"></a><span data-ttu-id="eb598-131">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eb598-131">Remarks</span></span>

<span data-ttu-id="eb598-132">Aby uzyskać pełną specyfikację, zobacz [ \[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span><span class="sxs-lookup"><span data-stu-id="eb598-132">For the complete specification, see [\[MS-XAML\]](https://docs.microsoft.com/previous-versions/msp-n-p/ff650760(v=pandp.10)).</span></span>
