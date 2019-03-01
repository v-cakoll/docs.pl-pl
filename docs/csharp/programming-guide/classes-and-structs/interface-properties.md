---
title: Właściwości — interfejsu C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: dd3f935043622f59018c068916e2d27a818f2ae8
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964685"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="baa99-102">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="baa99-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="baa99-103">Właściwości mogą być deklarowane na [interfejsu](../../../csharp/language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="baa99-103">Properties can be declared on an [interface](../../../csharp/language-reference/keywords/interface.md).</span></span> <span data-ttu-id="baa99-104">Oto przykład metody dostępu właściwości interfejsu:</span><span class="sxs-lookup"><span data-stu-id="baa99-104">The following is an example of an interface property accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 <span data-ttu-id="baa99-105">Metoda dostępu właściwość interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="baa99-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="baa99-106">W związku z tym celem metody dostępu jest wskazuje, czy właściwość jest odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="baa99-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="baa99-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="baa99-107">Example</span></span>  
 <span data-ttu-id="baa99-108">W tym przykładzie interfejs `IEmployee` ma właściwość odczytu i zapisu, `Name`, a właściwość tylko do odczytu `Counter`.</span><span class="sxs-lookup"><span data-stu-id="baa99-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="baa99-109">Klasa `Employee` implementuje `IEmployee` interfejs i korzysta z tych dwóch właściwości.</span><span class="sxs-lookup"><span data-stu-id="baa99-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="baa99-110">Program odczytuje nazwę nowego pracownika i bieżącą liczbę pracowników i wyświetla nazwę pracowników i liczba pracowników obliczanej.</span><span class="sxs-lookup"><span data-stu-id="baa99-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="baa99-111">Można użyć w pełni kwalifikowaną nazwę właściwości, która odwołuje się do interfejsu, w którym zadeklarowany jest element członkowski.</span><span class="sxs-lookup"><span data-stu-id="baa99-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="baa99-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="baa99-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="baa99-113">Jest to nazywane [jawnej implementacji interfejsu](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="baa99-113">This is called [Explicit Interface Implementation](../../../csharp/programming-guide/interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="baa99-114">Na przykład jeśli klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i dotyczą obu interfejsów `Name` właściwości jawną implementacją członków będzie to konieczne.</span><span class="sxs-lookup"><span data-stu-id="baa99-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="baa99-115">Oznacza to, że następująca deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="baa99-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="baa99-116">implementuje `Name` właściwość `IEmployee` interfejsu podczas następującą deklarację:</span><span class="sxs-lookup"><span data-stu-id="baa99-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 <span data-ttu-id="baa99-117">implementuje `Name` właściwość `ICitizen` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="baa99-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](../../../csharp/programming-guide/classes-and-structs/codesnippet/CSharp/interface-properties_4.cs)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="baa99-118">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="baa99-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="baa99-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="baa99-119">See also</span></span>

- [<span data-ttu-id="baa99-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="baa99-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="baa99-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="baa99-121">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
- [<span data-ttu-id="baa99-122">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="baa99-122">Using Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/using-properties.md)
- [<span data-ttu-id="baa99-123">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="baa99-123">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="baa99-124">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="baa99-124">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)
- [<span data-ttu-id="baa99-125">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="baa99-125">Interfaces</span></span>](../../../csharp/programming-guide/interfaces/index.md)
