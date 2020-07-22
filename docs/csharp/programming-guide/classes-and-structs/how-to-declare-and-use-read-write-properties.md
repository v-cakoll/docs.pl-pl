---
title: Jak deklarować i używać właściwości odczytu zapisu — Przewodnik programowania w języku C#
description: Dowiedz się, jak używać właściwości odczytu/zapisu w języku C#. Ten przykład obejmuje dwie właściwości, z których każdy ma metody dostępu get i Set, dlatego właściwości są odczytywane i zapisywane.
ms.date: 07/20/2015
helpviewer_keywords:
- get accessor [C#], declaring properties
- set accessor [C#]
- properties [C#], declaring
- read/write properties [C#]
- accessors [C#], declaring properties with
ms.assetid: a4962fef-af7e-4c4b-a929-4ae4d646ab8a
ms.openlocfilehash: 08bdaa9446491d473cfb16e3b82bac41d7af5b79
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864452"
---
# <a name="how-to-declare-and-use-read-write-properties-c-programming-guide"></a><span data-ttu-id="92cdf-104">Jak deklarować i używać właściwości odczytu zapisu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="92cdf-104">How to declare and use read write properties (C# Programming Guide)</span></span>
<span data-ttu-id="92cdf-105">Właściwości zapewniają wygodę publicznych członków danych bez ryzyka związanego z niechronionym, niekontrolowanym i niezweryfikowanym dostępem do danych obiektu.</span><span class="sxs-lookup"><span data-stu-id="92cdf-105">Properties provide the convenience of public data members without the risks that come with unprotected, uncontrolled, and unverified access to an object's data.</span></span> <span data-ttu-id="92cdf-106">Jest to realizowane za pośrednictwem metod *dostępu*: specjalne metody, które przypisują i pobierają wartości z bazowego elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="92cdf-106">This is accomplished through *accessors*: special methods that assign and retrieve values from the underlying data member.</span></span> <span data-ttu-id="92cdf-107">Metoda dostępu [Set](../../language-reference/keywords/set.md) umożliwia składowe danych, a metoda dostępu [Get](../../language-reference/keywords/get.md) pobiera wartości elementu członkowskiego danych.</span><span class="sxs-lookup"><span data-stu-id="92cdf-107">The [set](../../language-reference/keywords/set.md) accessor enables data members to be assigned, and the [get](../../language-reference/keywords/get.md) accessor retrieves data member values.</span></span>  
  
 <span data-ttu-id="92cdf-108">Ten przykład pokazuje `Person` klasę, która ma dwie właściwości: `Name` (String) i `Age` (int).</span><span class="sxs-lookup"><span data-stu-id="92cdf-108">This sample shows a `Person` class that has two properties: `Name` (string) and `Age` (int).</span></span> <span data-ttu-id="92cdf-109">Obie właściwości zapewniają `get` i metody `set` dostępu, więc są uznawane za właściwości odczytu i zapisu.</span><span class="sxs-lookup"><span data-stu-id="92cdf-109">Both properties provide `get` and `set` accessors, so they are considered read/write properties.</span></span>  
  
## <a name="example"></a><span data-ttu-id="92cdf-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="92cdf-110">Example</span></span>  
 [!code-csharp[csProgGuideObjects#33](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#33)]  
  
## <a name="robust-programming"></a><span data-ttu-id="92cdf-111">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="92cdf-111">Robust Programming</span></span>  
 <span data-ttu-id="92cdf-112">W poprzednim przykładzie `Name` `Age` właściwości i są [publiczne](../../language-reference/keywords/public.md) i zawierają `get` `set` metodę dostępu a i.</span><span class="sxs-lookup"><span data-stu-id="92cdf-112">In the previous example, the `Name` and `Age` properties are [public](../../language-reference/keywords/public.md) and include both a `get` and a `set` accessor.</span></span> <span data-ttu-id="92cdf-113">Dzięki temu każdy obiekt może odczytywać i zapisywać te właściwości.</span><span class="sxs-lookup"><span data-stu-id="92cdf-113">This allows any object to read and write these properties.</span></span> <span data-ttu-id="92cdf-114">Jednak czasami pożądane jest wyłączenie jednego z metod dostępu.</span><span class="sxs-lookup"><span data-stu-id="92cdf-114">It is sometimes desirable, however, to exclude one of the accessors.</span></span> <span data-ttu-id="92cdf-115">Z pominięciem `set` metody dostępu, na przykład, powoduje, że właściwość jest tylko do odczytu:</span><span class="sxs-lookup"><span data-stu-id="92cdf-115">Omitting the `set` accessor, for example, makes the property read-only:</span></span>  
  
 [!code-csharp[csProgGuideObjects#87](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#87)]  
  
 <span data-ttu-id="92cdf-116">Alternatywnie można uwidocznić jeden akcesor publicznie, ale drugi prywatny lub chroniony.</span><span class="sxs-lookup"><span data-stu-id="92cdf-116">Alternatively, you can expose one accessor publicly but make the other private or protected.</span></span> <span data-ttu-id="92cdf-117">Aby uzyskać więcej informacji, zobacz [ułatwienia dostępu asymetryczny](./restricting-accessor-accessibility.md).</span><span class="sxs-lookup"><span data-stu-id="92cdf-117">For more information, see [Asymmetric Accessor Accessibility](./restricting-accessor-accessibility.md).</span></span>  
  
 <span data-ttu-id="92cdf-118">Po zadeklarowaniu właściwości można ich używać tak, jakby były polami klasy.</span><span class="sxs-lookup"><span data-stu-id="92cdf-118">Once the properties are declared, they can be used as if they were fields of the class.</span></span> <span data-ttu-id="92cdf-119">Pozwala to na bardzo naturalną składnię podczas pobierania i ustawiania wartości właściwości, jak w następujących instrukcjach:</span><span class="sxs-lookup"><span data-stu-id="92cdf-119">This allows for a very natural syntax when both getting and setting the value of a property, as in the following statements:</span></span>  
  
 [!code-csharp[csProgGuideObjects#35](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#35)]  
  
 <span data-ttu-id="92cdf-120">Należy pamiętać, że w `set` metodzie właściwości `value` jest dostępna specjalna zmienna.</span><span class="sxs-lookup"><span data-stu-id="92cdf-120">Note that in a property `set` method a special `value` variable is available.</span></span> <span data-ttu-id="92cdf-121">Ta zmienna zawiera wartość określoną przez użytkownika, na przykład:</span><span class="sxs-lookup"><span data-stu-id="92cdf-121">This variable contains the value that the user specified, for example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#36](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#36)]  
  
 <span data-ttu-id="92cdf-122">Zwróć uwagę na czystą składnię zwiększającą `Age` Właściwość `Person` obiektu:</span><span class="sxs-lookup"><span data-stu-id="92cdf-122">Notice the clean syntax for incrementing the `Age` property on a `Person` object:</span></span>  
  
 [!code-csharp[csProgGuideObjects#37](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#37)]  
  
 <span data-ttu-id="92cdf-123">Jeśli `set` `get` do właściwości modelu użyto oddzielnych metod i, odpowiedni kod może wyglądać następująco:</span><span class="sxs-lookup"><span data-stu-id="92cdf-123">If separate `set` and `get` methods were used to model properties, the equivalent code might look like this:</span></span>  
  
```csharp  
person.SetAge(person.GetAge() + 1);
```  
  
 <span data-ttu-id="92cdf-124">`ToString`Metoda została przesłonięta w tym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="92cdf-124">The `ToString` method is overridden in this example:</span></span>  
  
 [!code-csharp[csProgGuideObjects#38](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideObjects/CS/Objects.cs#38)]  
  
 <span data-ttu-id="92cdf-125">Należy zauważyć, że `ToString` nie jest on jawnie używany w programie.</span><span class="sxs-lookup"><span data-stu-id="92cdf-125">Notice that `ToString` is not explicitly used in the program.</span></span> <span data-ttu-id="92cdf-126">Jest wywoływana domyślnie przez `WriteLine` wywołania.</span><span class="sxs-lookup"><span data-stu-id="92cdf-126">It is invoked by default by the `WriteLine` calls.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92cdf-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="92cdf-127">See also</span></span>

- [<span data-ttu-id="92cdf-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="92cdf-128">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="92cdf-129">Właściwości</span><span class="sxs-lookup"><span data-stu-id="92cdf-129">Properties</span></span>](./properties.md)
- [<span data-ttu-id="92cdf-130">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="92cdf-130">Classes and Structs</span></span>](./index.md)
