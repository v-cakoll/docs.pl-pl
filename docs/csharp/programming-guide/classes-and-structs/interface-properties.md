---
title: Właściwości interfejsu — C# Przewodnik programowania
ms.date: 01/31/2020
helpviewer_keywords:
- properties [C#], on interfaces
- interfaces [C#], properties
ms.assetid: 6503e9ed-33d7-44ec-b4c1-cc16c084b795
ms.openlocfilehash: 5798b80526f34e923e2eaab43847b98f6c64e14b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77626623"
---
# <a name="interface-properties-c-programming-guide"></a><span data-ttu-id="d2b0a-102">Właściwości interfejsu (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d2b0a-102">Interface Properties (C# Programming Guide)</span></span>

<span data-ttu-id="d2b0a-103">Właściwości można zadeklarować w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="d2b0a-103">Properties can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="d2b0a-104">Poniższy przykład deklaruje metodę dostępu do właściwości interfejsu:</span><span class="sxs-lookup"><span data-stu-id="d2b0a-104">The following example declares an interface property accessor:</span></span>

[!code-csharp[DeclareProperties](~/samples/snippets/csharp/interfaces/properties.cs#DeclareInterfaceProperties)]

<span data-ttu-id="d2b0a-105">Właściwości interfejsu zazwyczaj nie mają treści.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-105">Interface properties typically don't have a body.</span></span> <span data-ttu-id="d2b0a-106">Metody dostępu wskazują, czy właściwość jest tylko do odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-106">The accessors indicate whether the property is read-write, read-only, or write-only.</span></span> <span data-ttu-id="d2b0a-107">W przeciwieństwie do klas i struktur, deklarując metody dostępu bez treści nie deklaruje właściwości, która jest [implementowana](auto-implemented-properties.md).</span><span class="sxs-lookup"><span data-stu-id="d2b0a-107">Unlike in classes and structs, declaring the accessors without a body doesn't declare an [auto-implemented property](auto-implemented-properties.md).</span></span> <span data-ttu-id="d2b0a-108">Począwszy od C# 8,0, interfejs może definiować domyślną implementację elementów członkowskich, w tym właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-108">Beginning with C# 8.0, an interface may define a default implementation for members, including properties.</span></span> <span data-ttu-id="d2b0a-109">Definiowanie domyślnej implementacji właściwości w interfejsie jest rzadkie, ponieważ interfejsy nie mogą definiować pól danych wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-109">Defining a default implementation for a property in an interface is rare because interfaces may not define instance data fields.</span></span>

## <a name="example"></a><span data-ttu-id="d2b0a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="d2b0a-110">Example</span></span>

<span data-ttu-id="d2b0a-111">W tym przykładzie interfejs `IEmployee` ma właściwość do odczytu i zapisu, `Name`i właściwość tylko do odczytu, `Counter`.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-111">In this example, the interface `IEmployee` has a read-write property, `Name`, and a read-only property, `Counter`.</span></span> <span data-ttu-id="d2b0a-112">Klasa `Employee` implementuje interfejs `IEmployee` i używa tych dwóch właściwości.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-112">The class `Employee` implements the `IEmployee` interface and uses these two properties.</span></span> <span data-ttu-id="d2b0a-113">Program odczytuje nazwę nowego pracownika oraz bieżącą liczbę pracowników i wyświetla nazwę pracownika oraz obliczony numer pracownika.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-113">The program reads the name of a new employee and the current number of employees and displays the employee name and the computed employee number.</span></span>

<span data-ttu-id="d2b0a-114">Można użyć w pełni kwalifikowanej nazwy właściwości, która odwołuje się do interfejsu, w którym jest zadeklarowany element członkowski.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-114">You could use the fully qualified name of the property, which references the interface in which the member is declared.</span></span> <span data-ttu-id="d2b0a-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d2b0a-115">For example:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="d2b0a-116">W powyższym przykładzie przedstawiono [jawną implementację interfejsu](../interfaces/explicit-interface-implementation.md).</span><span class="sxs-lookup"><span data-stu-id="d2b0a-116">The preceding example demonstrates [Explicit Interface Implementation](../interfaces/explicit-interface-implementation.md).</span></span> <span data-ttu-id="d2b0a-117">Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy `ICitizen` i `IEmployee` i oba interfejsy mają właściwość `Name`, wymagana jest Jawna implementacja elementów członkowskich interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-117">For example, if the class `Employee` is implementing two interfaces `ICitizen` and `IEmployee` and both interfaces have the `Name` property, the explicit interface member implementation will be necessary.</span></span> <span data-ttu-id="d2b0a-118">Oznacza to, że następująca deklaracja właściwości:</span><span class="sxs-lookup"><span data-stu-id="d2b0a-118">That is, the following property declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#ExplicitImplementation)]

<span data-ttu-id="d2b0a-119">implementuje Właściwość `Name` w interfejsie `IEmployee`, podczas gdy następująca deklaracja:</span><span class="sxs-lookup"><span data-stu-id="d2b0a-119">implements the `Name` property on the `IEmployee` interface, while the following declaration:</span></span>

[!code-csharp[ExplicitProperties](~/samples/snippets/csharp/interfaces/properties.cs#CitizenImplementation)]

<span data-ttu-id="d2b0a-120">implementuje Właściwość `Name` w interfejsie `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="d2b0a-120">implements the `Name` property on the `ICitizen` interface.</span></span>

[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#PropertyExample)]
[!code-csharp[Example](~/samples/snippets/csharp/interfaces/properties.cs#UseProperty)]

**`210 Hazem Abolrous`**

## <a name="sample-output"></a><span data-ttu-id="d2b0a-121">Przykładowe dane wyjściowe</span><span class="sxs-lookup"><span data-stu-id="d2b0a-121">Sample output</span></span>

```console
Enter number of employees: 210
Enter the name of the new employee: Hazem Abolrous
The employee information:
Employee number: 211
Employee name: Hazem Abolrous
```

## <a name="see-also"></a><span data-ttu-id="d2b0a-122">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2b0a-122">See also</span></span>

- [<span data-ttu-id="d2b0a-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d2b0a-123">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="d2b0a-124">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d2b0a-124">Properties</span></span>](./properties.md)
- [<span data-ttu-id="d2b0a-125">Używanie właściwości</span><span class="sxs-lookup"><span data-stu-id="d2b0a-125">Using Properties</span></span>](./using-properties.md)
- [<span data-ttu-id="d2b0a-126">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="d2b0a-126">Comparison Between Properties and Indexers</span></span>](../indexers/comparison-between-properties-and-indexers.md)
- <span data-ttu-id="d2b0a-127">[Indexers](../indexers/index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="d2b0a-127">[Indexers](../indexers/index.md)</span></span>
- [<span data-ttu-id="d2b0a-128">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d2b0a-128">Interfaces</span></span>](../interfaces/index.md)
