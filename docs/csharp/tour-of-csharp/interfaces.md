---
title: "Interfejsy języka C# — samouczek języka C#"
description: "Interfejsy Definiowanie kontraktów zaimplementowanych przez typy w języku C#"
keywords: ".NET, csharp, interfejsów, dziedziczenie wielokrotne polimorfizm"
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 673ac56f3f5732fcda02d313b6f4273708ae365f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="interfaces"></a><span data-ttu-id="1c7d9-104">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1c7d9-104">Interfaces</span></span>

<span data-ttu-id="1c7d9-105">***Interfejsu*** definiuje kontrakt może być zaimplementowany przez klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-105">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="1c7d9-106">Interfejs może zawierać metod, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-106">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="1c7d9-107">Interfejs nie zawiera implementacji elementów członkowskich definiuje — Określa on tylko elementy członkowskie, które muszą zostać dostarczone przez klasy lub struktury, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-107">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="1c7d9-108">Interfejsy mogą stosować ***dziedziczenie wielokrotne***.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-108">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="1c7d9-109">W poniższym przykładzie interfejsu `IComboBox` dziedziczy z obu `ITextBox` i `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-109">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="1c7d9-110">Klasy i struktury można zaimplementować wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-110">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="1c7d9-111">W poniższym przykładzie klasa `EditBox` implementuje zarówno `IControl` i `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-111">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="1c7d9-112">Po klasie lub strukturze implementuje konkretnego interfejsu, wystąpień tej klasy lub struktury można niejawnie przekonwertowana na typ tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-112">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="1c7d9-113">Na przykład</span><span class="sxs-lookup"><span data-stu-id="1c7d9-113">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="1c7d9-114">W przypadkach, gdy wystąpienie jest statycznie nieznany do zaimplementowania konkretnego interfejsu można użyć rzutowania typów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-114">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="1c7d9-115">Na przykład następujące instrukcje umożliwia rzutowania z typu dynamicznego uzyskanie obiektu `IControl` i `IDataBound` implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-115">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="1c7d9-116">Ponieważ środowiska wykonawczego rzeczywisty typ obiektu to `EditBox`, rzutowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-116">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="1c7d9-117">W poprzednim `EditBox` klasy `Paint` metody z `IControl` interfejsu i `Bind` metody z `IDataBound` interfejsu są implementowane za pomocą publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-117">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="1c7d9-118">C# obsługuje również jawne ***implementacje elementów członkowskich interfejsu***, włączanie klasy lub struktury, aby uniknąć publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-118">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="1c7d9-119">Implementacja interfejsu jawnego członka jest zapisywany przy użyciu interfejsu w pełni kwalifikowaną nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-119">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="1c7d9-120">Na przykład `EditBox` można zaimplementować klasy `IControl.Paint` i `IDataBound.Bind` metody za pomocą jawnego interfejsu implementacje elementów członkowskich w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-120">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="1c7d9-121">Elementy członkowskie interfejsu jawnego można uzyskać tylko za pośrednictwem typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-121">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="1c7d9-122">Na przykład stosowania `IControl.Paint` dostarczane przez poprzednie pole edycji można wywołać tylko klasy konwertując pierwszy `EditBox` odwołanie do `IControl` typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1c7d9-122">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="1c7d9-123">[Poprzednie](arrays.md)
[dalej](enums.md)</span><span class="sxs-lookup"><span data-stu-id="1c7d9-123">[Previous](arrays.md)
[Next](enums.md)</span></span>
