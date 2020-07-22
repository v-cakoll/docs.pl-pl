---
title: Właściwości interfejsu — Przewodnik programowania w języku C#
description: Właściwości mogą być deklarowane w interfejsie w języku C#. Ten przykład deklaruje metodę dostępu do właściwości interfejsu.
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 920381ae804a6a968bfd667171269377f3d7e448
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86864972"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="c9a9a-104">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c9a9a-104">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="c9a9a-105">Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="c9a9a-105">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="c9a9a-106">Poniższy przykład deklaruje metodę dostępu do właściwości interfejsu:</span><span class="sxs-lookup"><span data-stu-id="c9a9a-106">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="c9a9a-107">Właściwości interfejsu zazwyczaj nie mają treści.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-107">Interface properties typically don't have a body.</span></span> <span data-ttu-id="c9a9a-108">Metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-108">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="c9a9a-109">W przeciwieństwie do klas i struktur, deklarując metody dostępu bez treści nie deklaruje właściwości, która jest [implementowana](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="c9a9a-109">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="c9a9a-110">Począwszy od języka C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich, w tym właściwości.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-110">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="c9a9a-111">Definiowanie domyślnej implementacji właściwości w interfejsie jest rzadkie, ponieważ interfejsy nie mogą definiować pól danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-111">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="c9a9a-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="c9a9a-112">Example</span></span>

<span data-ttu-id="c9a9a-113">W tym przykładzie interfejs `IEmployee` ma właściwość do odczytu i zapisu `Name` oraz właściwość tylko do odczytu `Counter` .</span><span class="sxs-lookup"><span data-stu-id="c9a9a-113">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="c9a9a-114">Klasa `Employee` implementuje `IEmployee` interfejs i używa tych dwóch właściwości.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-114">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="c9a9a-115">Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-115">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="c9a9a-116">Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-116">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="c9a9a-117">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c9a9a-117">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="c9a9a-118">W powyższym przykładzie przedstawiono [jawną implementację interfejsu](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="c9a9a-118">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="c9a9a-119">Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` oba interfejsy mają `Name` Właściwość, wymagana jest Jawna implementacja elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-119">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="c9a9a-120">Oznacza to, że następująca deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="c9a9a-120">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="c9a9a-121">implementuje `Name` Właściwość w `IEmployee` interfejsie, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="c9a9a-121">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="c9a9a-122">implementuje `Name` Właściwość w `ICitizen` interfejsie.</span><span class="sxs-lookup"><span data-stu-id="c9a9a-122">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="c9a9a-123">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="c9a9a-123">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="c9a9a-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c9a9a-124">See also</span></span>

- [<span data-ttu-id="c9a9a-125">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c9a9a-125">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="c9a9a-126">Właściwości</span><span class="sxs-lookup"><span data-stu-id="c9a9a-126">Properties</span></span>](./properties.md)
- [<span data-ttu-id="c9a9a-127">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="c9a9a-127">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="c9a9a-128">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="c9a9a-128">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- [<span data-ttu-id="c9a9a-129">Indexers (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="c9a9a-129">Indexers</span></span>](../indexers/index.md)
- [<span data-ttu-id="c9a9a-130">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="c9a9a-130">Interfaces</span></span>](../interfaces/index.md)
