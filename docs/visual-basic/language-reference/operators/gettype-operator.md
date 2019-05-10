---
title: GetType — Operator (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
ms.openlocfilehash: 3366a0d1a90667cf1d9b58b211892ad264849c59
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64633248"
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="5b4ae-102">GetType — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5b4ae-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="5b4ae-103">Zwraca <xref:System.Type> obiektu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="5b4ae-104"><xref:System.Type> Obiekt zawiera informacje o typie, takie jak jego właściwości, metody i zdarzenia.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b4ae-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="5b4ae-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
## <a name="parameters"></a><span data-ttu-id="5b4ae-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="5b4ae-106">Parameters</span></span>  
  
|<span data-ttu-id="5b4ae-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="5b4ae-107">Parameter</span></span>|<span data-ttu-id="5b4ae-108">Opis</span><span class="sxs-lookup"><span data-stu-id="5b4ae-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="5b4ae-109">Nazwa typu, dla którego chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5b4ae-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5b4ae-110">Remarks</span></span>  
 <span data-ttu-id="5b4ae-111">`GetType` Operator zwraca <xref:System.Type> obiektu dla określonego `typename`.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="5b4ae-112">Można przekazać nazwę typu zdefiniowanego w `typename`.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="5b4ae-113">Uwzględnione są następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="5b4ae-113">This includes the following:</span></span>  
  
- <span data-ttu-id="5b4ae-114">Typ danych dowolnego języka Visual Basic, takie jak `Boolean` lub `Date`.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
- <span data-ttu-id="5b4ae-115">Wszelkie .NET Framework klasy, struktury, moduł lub interfejsu, takich jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="5b4ae-116">Wszystkie klasy, struktury, modułu lub interfejsem zdefiniowanym przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
- <span data-ttu-id="5b4ae-117">Tablica, wszelkie zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-117">Any array defined by your application.</span></span>  
  
- <span data-ttu-id="5b4ae-118">Dowolnym delegatem, który zdefiniowano w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-118">Any delegate defined by your application.</span></span>  
  
- <span data-ttu-id="5b4ae-119">Wyliczenie, wszelkie zdefiniowane przez Visual Basic, .NET Framework lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="5b4ae-120">Aby uzyskać obiekt typu zmiennej obiektu, należy użyć <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="5b4ae-121">`GetType` Operator może być przydatne w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="5b4ae-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
- <span data-ttu-id="5b4ae-122">Należy uzyskać dostęp do metadanych dla typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="5b4ae-123"><xref:System.Type> Obiektu dostarcza metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="5b4ae-124">Jest to potrzebne, na przykład, aby odzwierciedlić za pośrednictwem zestawu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="5b4ae-125">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
- <span data-ttu-id="5b4ae-126">Chcesz porównać dwa odwołania do obiektu, aby sprawdzić, czy odnoszą się do wystąpienia tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="5b4ae-127">Jeśli tak, `GetType` zwraca odwołania do tej samej <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5b4ae-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="5b4ae-128">Example</span></span>  
 <span data-ttu-id="5b4ae-129">W poniższych przykładach pokazano `GetType` operatora w użyciu.</span><span class="sxs-lookup"><span data-stu-id="5b4ae-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#26)]  
  
## <a name="see-also"></a><span data-ttu-id="5b4ae-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5b4ae-130">See also</span></span>

- [<span data-ttu-id="5b4ae-131">Pierwszeństwo operatorów w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="5b4ae-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [<span data-ttu-id="5b4ae-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="5b4ae-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [<span data-ttu-id="5b4ae-133">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="5b4ae-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
