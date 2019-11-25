---
title: Jak deklarować i używać właściwości odczytu zapisu — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 2865feb74692e7075c92a9ee2b5cd2a7735a8e62
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971012"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="86499-102">Jak deklarować i używać właściwości odczytu zapisu (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="86499-102">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="86499-103">Właściwości zapewniają wygodę publicznych członków danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="86499-103">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="86499-104">Jest to realizowane za pośrednictwem metod *dostępu*: specjalne metody, które przypisują i pobierają wartości z bazowego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="86499-104">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="86499-105">Metoda dostępu [Set](../../language-reference/keywords/set.md) umożliwia składowe danych, a metoda dostępu [Get](../../language-reference/keywords/get.md) pobiera wartości elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="86499-105">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="86499-106">Ten przykład pokazuje klasę `Person`, która ma dwie właściwości: `Name` (String) i `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="86499-106">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="86499-107">Obie właściwości zapewniają `get` i `set` metod dostępu, więc są uznawane za właściwości odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="86499-107">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86499-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="86499-108">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="86499-109">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="86499-109">Robust Programming</span></span>  
 <span data-ttu-id="86499-110">W poprzednim przykładzie właściwości `Name` i `Age` są [publiczne](../../language-reference/keywords/public.md) i obejmują zarówno `get` jak i `set` metodę dostępu.</span><span class="sxs-lookup"><span data-stu-id="86499-110">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="86499-111">Dzięki temu każdy obiekt może odczytywać i zapisywać te właściwości.</span><span class="sxs-lookup"><span data-stu-id="86499-111">This allows any object to read and write these properties.</span></span> <span data-ttu-id="86499-112">Jednak czasami pożądane jest wyłączenie jednego z metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="86499-112">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="86499-113">Z pominięciem metody dostępu `set`, na przykład, powoduje, że właściwość jest tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="86499-113">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="86499-114">Alternatywnie można uwidocznić jeden akcesor publicznie, ale drugi prywatny lub chroniony.</span><span class="sxs-lookup"><span data-stu-id="86499-114">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="86499-115">Aby uzyskać więcej informacji, zobacz [ułatwienia dostępu asymetryczny](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="86499-115">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="86499-116">Po zadeklarowaniu właściwości można ich używać tak, jakby były polami klasy.</span><span class="sxs-lookup"><span data-stu-id="86499-116">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="86499-117">Pozwala to na bardzo naturalną składnię podczas pobierania i ustawiania wartości właściwości, jak w następujących instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="86499-117">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="86499-118">Należy zauważyć, że w metodzie `set` właściwość jest dostępna specjalna `value` zmienna.</span><span class="sxs-lookup"><span data-stu-id="86499-118">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="86499-119">Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:</span><span class="sxs-lookup"><span data-stu-id="86499-119">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="86499-120">Zwróć uwagę na czystą składnię zwiększającą Właściwość `Age` w obiekcie `Person`:</span><span class="sxs-lookup"><span data-stu-id="86499-120">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="86499-121">Jeśli do właściwości modelu użyto oddzielnych metod `set` i `get`, odpowiedni kod może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="86499-121">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);   
```  
  
 <span data-ttu-id="86499-122">Metoda `ToString` została przesłonięta w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="86499-122">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="86499-123">Zwróć uwagę, że `ToString` nie jest jawnie używana w programie.</span><span class="sxs-lookup"><span data-stu-id="86499-123">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="86499-124">Jest ona wywoływana domyślnie przez wywołania `WriteLine`.</span><span class="sxs-lookup"><span data-stu-id="86499-124">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="86499-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86499-125">See also</span></span>

- [<span data-ttu-id="86499-126">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="86499-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="86499-127">Właściwości</span><span class="sxs-lookup"><span data-stu-id="86499-127">Properties</span></span>](./properties.md)
- [<span data-ttu-id="86499-128">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="86499-128">Classes and Structs</span></span>](./index.md)
