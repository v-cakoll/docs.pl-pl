---
title: Właściwości interfejsu — C# Przewodnik programowania
ms.date: 07/20/2015
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: ff892a35f4be6600c00bc0c72c2f789ef6eb4408
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75705538"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="a17a5-102">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a17a5-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="a17a5-103">Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="a17a5-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="a17a5-104">Oto przykład metody dostępu do właściwości interfejsu:</span><span class="sxs-lookup"><span data-stu-id="a17a5-104">The following is an example of an interface property accessor:</span></span>

[!code-csharp[csProgGuideProperties#14](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#14)]

<span data-ttu-id="a17a5-105">Metoda dostępu do właściwości interfejsu nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="a17a5-105">The accessor of an interface property does not have a body.</span></span> <span data-ttu-id="a17a5-106">W tym celu metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu, czy tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="a17a5-106">Thus, the purpose of the accessors is to indicate whether the property is read-write, read-only, or write-only.</span></span>

## <a name="example"></a><span data-ttu-id="a17a5-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="a17a5-107">Example</span></span>

<span data-ttu-id="a17a5-108">W tym przykładzie interfejs `IEmployee` ma właściwość do odczytu i zapisu, `Name`i właściwość tylko do odczytu, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="a17a5-108">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="a17a5-109">Klasa `Employee` implementuje interfejs `IEmployee` i używa tych dwóch właściwości.</span><span class="sxs-lookup"><span data-stu-id="a17a5-109">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="a17a5-110">Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="a17a5-110">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="a17a5-111">Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski.</span><span class="sxs-lookup"><span data-stu-id="a17a5-111">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="a17a5-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="a17a5-112">For example:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="a17a5-113">Ta nazwa jest nazywana [jawnym implementacją interfejsu](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="a17a5-113">This is called [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="a17a5-114">Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i oba interfejsy mają właściwość `Name`, wymagana jest Jawna implementacja elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="a17a5-114">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="a17a5-115">Oznacza to, że następująca deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="a17a5-115">That is, the following property declaration:</span></span>

[!code-csharp[csProgGuideProperties#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#16)]

<span data-ttu-id="a17a5-116">implementuje Właściwość `Name` w interfejsie `IEmployee`, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="a17a5-116">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[csProgGuideProperties#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#17)]

<span data-ttu-id="a17a5-117">implementuje Właściwość `Name` w interfejsie `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="a17a5-117">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[csProgGuideProperties#15](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuideProperties/CS/Properties.cs#15)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="a17a5-118">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="a17a5-118">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="a17a5-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a17a5-119">See also</span></span>

- [<span data-ttu-id="a17a5-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a17a5-120">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a17a5-121">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a17a5-121">Properties</span></span>](./properties.md)
- [<span data-ttu-id="a17a5-122">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="a17a5-122">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="a17a5-123">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="a17a5-123">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="a17a5-124">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="a17a5-124">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="a17a5-125">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="a17a5-125">Interfaces</span></span>](../interfaces/index.md)
