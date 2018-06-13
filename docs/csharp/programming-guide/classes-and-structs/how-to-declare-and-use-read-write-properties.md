---
title: 'Porady: deklarowanie i użycie właściwości do odczytu i zapisu (C# przewodnik programowania w języku)'
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: d6a7083e1c0cf0dc5c076a69dee15fc39e234d53
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172331"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="9e6bd-102">Porady: deklarowanie i użycie właściwości do odczytu i zapisu (C# przewodnik programowania w języku)</span><span class="sxs-lookup"><span data-stu-id="9e6bd-102">How to: Declare and Use Read Write Properties (C# Programming Guide)</span></span>
<span data-ttu-id="9e6bd-103">Właściwości wygodniejszego publiczne elementy członkowskie danych bez zagrożenie niechronione, niekontrolowanego i niezweryfikowane dostęp do danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="9e6bd-104">Jest to realizowane przez *akcesorów*: specjalne metody przypisać i pobrać wartości z podstawowego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="9e6bd-105">[Ustawić](../../../csharp/language-reference/keywords/set.md) dostępu umożliwia członkom danych można przypisać i [uzyskać](../../../csharp/language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-105">The [set](../../../csharp/language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../../csharp/language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="9e6bd-106">W tym przykładzie pokazano `Person` klasy, która ma dwie właściwości: `Name` (ciąg) i `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="9e6bd-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="9e6bd-107">Podaj zarówno właściwości `get` i `set` metody dostępu, więc są traktowane jako właściwości odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9e6bd-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="9e6bd-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_1.cs)]  
  
## <a name="robust-programming"></a><span data-ttu-id="9e6bd-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="9e6bd-109">Robust Programming</span></span>  
 <span data-ttu-id="9e6bd-110">W poprzednim przykładzie `Name` i `Age` właściwości są [publicznego](../../../csharp/language-reference/keywords/public.md) i zawiera zarówno `get` i `set` metody dostępu.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-110">In the previous example, the `Name` and `Age` properties are [public](../../../csharp/language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="9e6bd-111">Dzięki temu dowolnego obiektu do odczytu i zapisu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="9e6bd-112">Czasami jest pożądane, jednak do wykluczenia z jednej z metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="9e6bd-113">Pominięcie `set` dostępu, na przykład sprawia, że właściwość tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_2.cs)]  
  
 <span data-ttu-id="9e6bd-114">Alternatywnie można ujawnić publicznie jedną metodę dostępu, ale innych prywatne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="9e6bd-115">Aby uzyskać więcej informacji, zobacz [asymetrycznego dostępności metody dostępu](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="9e6bd-115">For more information, see [Asymmetric Accessor Accessibility](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="9e6bd-116">Po zadeklarowaniu są właściwości, użyciem tak, jakby były pola klasy.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="9e6bd-117">Dzięki temu bardzo fizycznych składni, gdy zarówno pobieranie i ustawianie wartości właściwości, jak następujące instrukcje:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_3.cs)]  
  
 <span data-ttu-id="9e6bd-118">Należy pamiętać, że we właściwości `set` metody a specjalne `value` zmienna jest dostępna.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="9e6bd-119">Ta zmienna uwzględnia wartość określonej przez użytkownika, na przykład:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_4.cs)]  
  
 <span data-ttu-id="9e6bd-120">Zwróć uwagę, czysta składnia zwiększanie `Age` właściwość `Person` obiektu:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_5.cs)]  
  
 <span data-ttu-id="9e6bd-121">Jeśli oddzielnych `set` i `get` metody zostały użyte do modelowania właściwości, równoważny kod może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="9e6bd-122">`ToString` Metoda zostanie przesłonięta w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9e6bd-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/how-to-declare-and-use-read-write-properties_6.cs)]  
  
 <span data-ttu-id="9e6bd-123">Zwróć uwagę, że `ToString` jawnie nie jest używany w programie.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="9e6bd-124">Domyślnie następuje jej wywoływanie `WriteLine` wywołania.</span><span class="sxs-lookup"><span data-stu-id="9e6bd-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9e6bd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9e6bd-125">See Also</span></span>  
 [<span data-ttu-id="9e6bd-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9e6bd-126">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9e6bd-127">Właściwości</span><span class="sxs-lookup"><span data-stu-id="9e6bd-127">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)  
 [<span data-ttu-id="9e6bd-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="9e6bd-128">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
