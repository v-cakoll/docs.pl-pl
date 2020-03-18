---
title: Jak deklarować i używać właściwości odczytu zapisu - Przewodnik programowania C#
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 4b9db5f15746ab9a1f42239150c6783154723371
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79170289"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="cac65-102">Jak zadeklarować i używać właściwości odczytu zapisu (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="cac65-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="cac65-103">Właściwości zapewniają wygodę publicznych elementów członkowskich danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="cac65-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="cac65-104">Jest to realizowane za pomocą *akcesorów:* specjalne metody, które przypisują i pobierają wartości z podstawowego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="cac65-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="cac65-105">[Set](../../language-reference/keywords/set.md) akcesor umożliwia członków danych, które mają być przypisane, a [get](../../language-reference/keywords/get.md) akcesor pobiera wartości elementów członkowskich danych.</span><span class="sxs-lookup"><span data-stu-id="cac65-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="cac65-106">W tym `Person` przykładzie przedstawiono klasę, `Name` która ma `Age` dwie właściwości: (ciąg) i (int).</span><span class="sxs-lookup"><span data-stu-id="cac65-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="cac65-107">Obie właściwości `get` zapewniają `set` i akcesorów, więc są one uważane za właściwości odczytu/zapisu.</span><span class="sxs-lookup"><span data-stu-id="cac65-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cac65-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="cac65-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="cac65-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="cac65-109">Robust Programming</span></span>  
 <span data-ttu-id="cac65-110">W poprzednim przykładzie `Name` i `Age` właściwości są [publiczne](../../language-reference/keywords/public.md) i `get` obejmują `set` zarówno a, jak i akcesor.</span><span class="sxs-lookup"><span data-stu-id="cac65-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="cac65-111">Dzięki temu każdy obiekt do odczytu i zapisu tych właściwości.</span><span class="sxs-lookup"><span data-stu-id="cac65-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="cac65-112">Czasami pożądane jest jednak wykluczenie jednego z akcesorów.</span><span class="sxs-lookup"><span data-stu-id="cac65-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="cac65-113">Pomijanie akcesor, `set` na przykład sprawia, że właściwość tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="cac65-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="cac65-114">Alternatywnie można udostępnić jeden akcesor publicznie, ale inne prywatne lub chronione.</span><span class="sxs-lookup"><span data-stu-id="cac65-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="cac65-115">Aby uzyskać więcej informacji, zobacz [Dostępność asymetrycznego dostępu](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="cac65-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="cac65-116">Po zadeklarowaniu właściwości mogą być używane tak, jakby były polami klasy.</span><span class="sxs-lookup"><span data-stu-id="cac65-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="cac65-117">Pozwala to na bardzo naturalną składnię, gdy zarówno uzyskanie i ustawienie wartości właściwości, jak w następujących instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="cac65-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="cac65-118">Należy zauważyć, `set` że w `value` metodzie właściwości dostępna jest specjalna zmienna.</span><span class="sxs-lookup"><span data-stu-id="cac65-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="cac65-119">Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:</span><span class="sxs-lookup"><span data-stu-id="cac65-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="cac65-120">Zwróć uwagę na czystą składnię zwiększania `Age` właściwości na `Person` obiekcie:</span><span class="sxs-lookup"><span data-stu-id="cac65-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="cac65-121">Jeśli `set` oddzielne `get` i metody zostały użyte do modelu właściwości, równoważny kod może wyglądać tak:</span><span class="sxs-lookup"><span data-stu-id="cac65-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="cac65-122">Metoda `ToString` jest zastąpiona w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cac65-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="cac65-123">Zwróć `ToString` uwagę, że nie jest jawnie używany w programie.</span><span class="sxs-lookup"><span data-stu-id="cac65-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="cac65-124">Jest wywoływana domyślnie `WriteLine` przez wywołania.</span><span class="sxs-lookup"><span data-stu-id="cac65-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cac65-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cac65-125">See also</span></span>

- [<span data-ttu-id="cac65-126">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="cac65-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="cac65-127">Właściwości</span><span class="sxs-lookup"><span data-stu-id="cac65-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="cac65-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="cac65-128">Classes and Structs</span></span>](./index.md)
