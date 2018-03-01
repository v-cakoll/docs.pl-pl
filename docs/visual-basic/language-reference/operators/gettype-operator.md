---
title: "GetType — Operator (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="857cc-102">GetType — Operator (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="857cc-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="857cc-103">Zwraca <xref:System.Type> obiektu określonego typu.</span><span class="sxs-lookup"><span data-stu-id="857cc-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="857cc-104"><xref:System.Type> Obiektu zawiera informacje o typie, takie jak jego właściwości, metod i zdarzeń.</span><span class="sxs-lookup"><span data-stu-id="857cc-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="857cc-105">Składnia</span><span class="sxs-lookup"><span data-stu-id="857cc-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="857cc-106">Parametry</span><span class="sxs-lookup"><span data-stu-id="857cc-106">Parameters</span></span>  
  
|<span data-ttu-id="857cc-107">Parametr</span><span class="sxs-lookup"><span data-stu-id="857cc-107">Parameter</span></span>|<span data-ttu-id="857cc-108">Opis</span><span class="sxs-lookup"><span data-stu-id="857cc-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="857cc-109">Nazwa typu, dla którego chcesz uzyskać informacje.</span><span class="sxs-lookup"><span data-stu-id="857cc-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="857cc-110">Uwagi</span><span class="sxs-lookup"><span data-stu-id="857cc-110">Remarks</span></span>  
 <span data-ttu-id="857cc-111">`GetType` Operator zwraca <xref:System.Type> obiektu dla określonego `typename`.</span><span class="sxs-lookup"><span data-stu-id="857cc-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="857cc-112">Można przekazać nazwę typu zdefiniowanego w `typename`.</span><span class="sxs-lookup"><span data-stu-id="857cc-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="857cc-113">Obejmuje to następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="857cc-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="857cc-114">Typ danych Visual Basic, takie jak `Boolean` lub `Date`.</span><span class="sxs-lookup"><span data-stu-id="857cc-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="857cc-115">.NET Framework klasy, struktury, moduł lub interfejsu, takich jak <xref:System.ArgumentException?displayProperty=nameWithType> lub <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="857cc-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="857cc-116">Wszystkie klasy, struktury, modułu lub interfejs zdefiniowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="857cc-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="857cc-117">Tablicy zdefiniowany przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="857cc-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="857cc-118">Delegat, wszelkie zdefiniowane przez aplikację.</span><span class="sxs-lookup"><span data-stu-id="857cc-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="857cc-119">Wszystkie wyliczenia zdefiniowanych przez Visual Basic, .NET Framework lub aplikacji.</span><span class="sxs-lookup"><span data-stu-id="857cc-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="857cc-120">Aby uzyskać obiekt typu zmiennej obiektu, należy użyć <xref:System.Type.GetType%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="857cc-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="857cc-121">`GetType` Operator może być przydatne w następujących okolicznościach:</span><span class="sxs-lookup"><span data-stu-id="857cc-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="857cc-122">Należy uzyskać dostępu do metadanych dla typu w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="857cc-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="857cc-123"><xref:System.Type> Obiektu udostępnia metadane, takie jak elementy członkowskie typu i informacje o wdrożeniu.</span><span class="sxs-lookup"><span data-stu-id="857cc-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="857cc-124">To konieczne, na przykład do uwzględnienia w zestawie.</span><span class="sxs-lookup"><span data-stu-id="857cc-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="857cc-125">Aby uzyskać więcej informacji, zobacz <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="857cc-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="857cc-126">Chcesz porównać dwa odwołania do obiektów, aby sprawdzić, czy odnoszą się do wystąpień tego samego typu.</span><span class="sxs-lookup"><span data-stu-id="857cc-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="857cc-127">Jeśli nie, `GetType` zwraca odwołania do tej samej <xref:System.Type> obiektu.</span><span class="sxs-lookup"><span data-stu-id="857cc-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="857cc-128">Przykład</span><span class="sxs-lookup"><span data-stu-id="857cc-128">Example</span></span>  
 <span data-ttu-id="857cc-129">W poniższych przykładach pokazano `GetType` operatora w użyciu.</span><span class="sxs-lookup"><span data-stu-id="857cc-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="857cc-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="857cc-130">See Also</span></span>  
 [<span data-ttu-id="857cc-131">Kolejność wykonywania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="857cc-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="857cc-132">Operatory według funkcji</span><span class="sxs-lookup"><span data-stu-id="857cc-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="857cc-133">Operatory i wyrażenia</span><span class="sxs-lookup"><span data-stu-id="857cc-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
