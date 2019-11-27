---
title: GetType, operator
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 4e59bcfaa24c9545ed75c6b5c1d29cad398ac2de
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349551"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="7bd09-102">GetType — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7bd09-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="7bd09-103">Zwraca obiekt <xref:System.Type> dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="7bd09-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="7bd09-104">Obiekt <xref:System.Type> zawiera informacje o typie, takim jak jego właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="7bd09-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7bd09-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="7bd09-105">Syntax</span></span>  
  
```vb  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="7bd09-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="7bd09-106">Parameters</span></span>  
  
|<span data-ttu-id="7bd09-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="7bd09-107">Parameter</span></span>|<span data-ttu-id="7bd09-108">Opis</span><span class="sxs-lookup"><span data-stu-id="7bd09-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="7bd09-109">Nazwa typu, dla którego chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="7bd09-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7bd09-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7bd09-110">Remarks</span></span>  
 <span data-ttu-id="7bd09-111">Operator `GetType` zwraca obiekt <xref:System.Type> dla określonego `typename`.</span><span class="sxs-lookup"><span data-stu-id="7bd09-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="7bd09-112">Można przekazać nazwę dowolnego zdefiniowanego typu w `typename`.</span><span class="sxs-lookup"><span data-stu-id="7bd09-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="7bd09-113">Uwzględnione są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="7bd09-113">This includes the following:</span></span>  
  
- <span data-ttu-id="7bd09-114">Dowolny Visual Basic typ danych, taki jak `Boolean` lub `Date`.</span><span class="sxs-lookup"><span data-stu-id="7bd09-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="7bd09-115">Wszelkie .NET Framework klasy, struktury, modułu lub interfejsu, takie jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7bd09-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="7bd09-116">Wszystkie klasy, struktury, moduły lub interfejsy zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7bd09-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="7bd09-117">Dowolna tablica zdefiniowana przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7bd09-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="7bd09-118">Każdy delegat zdefiniowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="7bd09-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="7bd09-119">Każde Wyliczenie zdefiniowane przez Visual Basic, .NET Framework lub aplikację.</span><span class="sxs-lookup"><span data-stu-id="7bd09-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="7bd09-120">Jeśli chcesz uzyskać obiekt typu zmiennej obiektu, użyj metody <xref:System.Type.GetType%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7bd09-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="7bd09-121">Operator `GetType` może być przydatny w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="7bd09-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="7bd09-122">Należy uzyskać dostęp do metadanych dla typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="7bd09-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="7bd09-123">Obiekt <xref:System.Type> dostarcza metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="7bd09-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="7bd09-124">Jest to konieczne, na przykład w celu odzwierciedlenia zestawu.</span><span class="sxs-lookup"><span data-stu-id="7bd09-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="7bd09-125">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7bd09-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="7bd09-126">Chcesz porównać dwa odwołania do obiektów, aby sprawdzić, czy odwołują się do wystąpień tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="7bd09-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="7bd09-127">Jeśli tak, `GetType` zwraca odwołania do tego samego obiektu <xref:System.Type>.</span><span class="sxs-lookup"><span data-stu-id="7bd09-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bd09-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="7bd09-128">Example</span></span>  
 <span data-ttu-id="7bd09-129">W poniższych przykładach pokazano operator `GetType` w użyciu.</span><span class="sxs-lookup"><span data-stu-id="7bd09-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="7bd09-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7bd09-130">See also</span></span>

- [<span data-ttu-id="7bd09-131">Pierwszeństwo operatorów w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7bd09-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="7bd09-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="7bd09-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="7bd09-133">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="7bd09-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
