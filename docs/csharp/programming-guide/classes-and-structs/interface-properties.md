---
title: Właściwości interfejsu — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: cdd425970442e284d6fd6488bbb13394c12e939a
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596451"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="4c902-102">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="4c902-102">Interface Properties (C# Programming Guide)</span></span>
<span data-ttu-id="4c902-103">Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="4c902-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="4c902-104">Oto przykład metody dostępu do właściwości interfejsu:</span><span class="sxs-lookup"><span data-stu-id="4c902-104">The following is an example of an interface property accessor:</span></span>  
  
 [!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]  
  
 <span data-ttu-id="4c902-105">Metoda dostępu do właściwości interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="4c902-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="4c902-106">W tym celu metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="4c902-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4c902-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="4c902-107">Example</span></span>  
 <span data-ttu-id="4c902-108">W tym przykładzie interfejs `IEmployee` ma `Name`właściwość do odczytu i zapisu oraz właściwość tylko do `Counter`odczytu.</span><span class="sxs-lookup"><span data-stu-id="4c902-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="4c902-109">`Employee` Klasa`IEmployee` implementuje interfejs i używa tych dwóch właściwości.</span><span class="sxs-lookup"><span data-stu-id="4c902-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="4c902-110">Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="4c902-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>  
  
 <span data-ttu-id="4c902-111">Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski.</span><span class="sxs-lookup"><span data-stu-id="4c902-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="4c902-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="4c902-112">For example:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="4c902-113">Ta nazwa jest nazywana [jawnym implementacją interfejsu](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="4c902-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="4c902-114">`Employee` Na przykład jeśli klasa implementuje dwa interfejsy `ICitizen` i `IEmployee` oba interfejsy mają `Name` właściwość, wymagana jest Jawna implementacja elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="4c902-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="4c902-115">Oznacza to, że następująca deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="4c902-115">That is, the following property declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]  
  
 <span data-ttu-id="4c902-116">`Name` implementuje właściwość `IEmployee` w interfejsie, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="4c902-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>  
  
 [!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]  
  
 <span data-ttu-id="4c902-117">`Name` implementuje właściwość `ICitizen` w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="4c902-117">implements the `Name` property on the `ICitizen` interface.</span></span>  
  
 [!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]  
  
  **`210 Hazem Abolrous`**    
## <a name="sample-output"></a><span data-ttu-id="4c902-118">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="4c902-118">Sample Output</span></span>  
 `Enter number of employees: 210`  
  
 `Enter the name of the new employee: Hazem Abolrous`  
  
 `The employee information:`  
  
 `Employee number: 211`  
  
 `Employee name: Hazem Abolrous`  
  
## <a name="see-also"></a><span data-ttu-id="4c902-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4c902-119">See also</span></span>

- [<span data-ttu-id="4c902-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4c902-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="4c902-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="4c902-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="4c902-122">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="4c902-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="4c902-123">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="4c902-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="4c902-124">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="4c902-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="4c902-125">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="4c902-125">Interfaces</span></span>](../interfaces/index.md)
