---
title: 'Instrukcje: Deklarowanie i użycie właściwości odczyt/zapis - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: b4dc9364e64f7ebfd495671b852b98d8f56c80b5
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56969043"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="0d6c3-102">Instrukcje: Deklarowanie i użycie właściwości odczyt/zapis (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="0d6c3-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="0d6c3-103">Właściwości zapewniają wygodne publiczne elementy członkowskie danych bez ryzyka związane z niechronionych, niekontrolowane i niezweryfikowanych dostęp do danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="0d6c3-104">Jest to realizowane za pośrednictwem *Akcesory*: specjalne metody, które przypisać i pobierania wartości z bazowego elementu danych.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="0d6c3-105">[Ustaw](../../../csharp/language-reference/keywords/set.md) dostępu umożliwia członkom danych można przypisać i [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="0d6c3-106">W tym przykładzie pokazano `Person` klasy, która ma dwie właściwości: `Name` (ciąg) i `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="0d6c3-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="0d6c3-107">Obie te właściwości zapewniają `get` i `set` metod dostępu, dzięki czemu są one traktowane jako właściwości odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d6c3-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="0d6c3-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="0d6c3-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="0d6c3-109">Robust Programming</span></span>  
 <span data-ttu-id="0d6c3-110">W poprzednim przykładzie `Name` i `Age` właściwości są [publicznych](../../../csharp/language-reference/keywords/public.md) i zawiera zarówno `get` i `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="0d6c3-111">Umożliwia to dowolnego obiektu odczytywać i zapisywać te właściwości.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="0d6c3-112">Czasami jest pożądane, jednak do wykluczenia z jednej z metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="0d6c3-113">Pominięcie `set` dostępu, na przykład sprawia, że właściwość tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="0d6c3-114">Alternatywnie można publicznie udostępnić jedną metodę dostępu, ale inne prywatnych lub chronionych.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="0d6c3-115">Aby uzyskać więcej informacji, zobacz [asymetrycznego dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="0d6c3-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="0d6c3-116">Po właściwości są deklarowane, mogą one używane tak, jakby były one pola klasy.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="0d6c3-117">Umożliwia to bardzo fizycznych składni, gdy zarówno pobierania i ustawiania wartości właściwości, tak jak w następujących instrukcji:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="0d6c3-118">Należy pamiętać, że we właściwości `set` typu specjalne `value` zmienna jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="0d6c3-119">Ta zmienna zawiera wartość, którą użytkownik określił, na przykład:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="0d6c3-120">Zwróć uwagę, czysta składnia zwiększanie `Age` właściwość `Person` obiektu:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="0d6c3-121">Jeśli jest to oddzielne `set` i `get` metody były używane do modelowania właściwości, równoważny kod może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="0d6c3-122">`ToString` Metoda zostanie przesłonięta w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="0d6c3-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="0d6c3-123">Należy zauważyć, że `ToString` jawnie nie jest używany w programie.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="0d6c3-124">Jest wywoływana, domyślnie `WriteLine` wywołania.</span><span class="sxs-lookup"><span data-stu-id="0d6c3-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0d6c3-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0d6c3-125">See also</span></span>

- [<span data-ttu-id="0d6c3-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0d6c3-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="0d6c3-127">Właściwości</span><span class="sxs-lookup"><span data-stu-id="0d6c3-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="0d6c3-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="0d6c3-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
