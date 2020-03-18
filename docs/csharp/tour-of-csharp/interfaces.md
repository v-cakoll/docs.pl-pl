---
title: C# Interfaces — przewodnik po języku Języka C#
description: 'Interfejsy definiują kontrakty implementowane według typów w języku C #'
ms.date: 02/27/2020
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 62d94462fa481379cf70d63a598deb7f36be204f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78159133"
---
# <a name="interfaces"></a><span data-ttu-id="7c300-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="7c300-103">Interfaces</span></span>

<span data-ttu-id="7c300-104">***Interfejs*** definiuje kontrakt, który może być implementowany przez klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="7c300-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="7c300-105">Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory.</span><span class="sxs-lookup"><span data-stu-id="7c300-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="7c300-106">Interfejs nie zapewnia implementacje elementów członkowskich definiuje — określa jedynie elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="7c300-106">An interface doesn't provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="7c300-107">Interfejsy mogą wykorzystywać ***wiele dziedziczenia***.</span><span class="sxs-lookup"><span data-stu-id="7c300-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="7c300-108">W poniższym przykładzie `IComboBox` interfejs dziedziczy z obu `ITextBox` i `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="7c300-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="7c300-109">Klasy i struktury można zaimplementować wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="7c300-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="7c300-110">W poniższym przykładzie `EditBox` klasa implementuje zarówno `IControl` i `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="7c300-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="7c300-111">Gdy klasa lub struktura implementuje określony interfejs, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane na ten typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c300-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="7c300-112">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7c300-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="7c300-113">W przypadkach, gdy wystąpienie nie jest statycznie znane do zaimplementowania określonego interfejsu, rzutowania typu dynamicznego mogą być używane.</span><span class="sxs-lookup"><span data-stu-id="7c300-113">In cases where an instance isn't statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="7c300-114">Na przykład następujące instrukcje użyć rzutowania typu dynamicznego, aby uzyskać implementacje obiektu `IControl` i `IDataBound` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c300-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="7c300-115">Ponieważ rzeczywisty typ obiektu w czasie `EditBox`wykonywania jest , rzuty powiedzie się.</span><span class="sxs-lookup"><span data-stu-id="7c300-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="7c300-116">W `EditBox` poprzedniej klasie `Paint` metoda `IControl` z interfejsu `Bind` i `IDataBound` metoda z interfejsu są implementowane przy użyciu elementów członkowskich publicznych.</span><span class="sxs-lookup"><span data-stu-id="7c300-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="7c300-117">C# obsługuje również ***implementacje elementu członkowskiego interfejsu***jawnego, umożliwiając klasy lub struktury, aby uniknąć upubliczniania elementów członkowskich.</span><span class="sxs-lookup"><span data-stu-id="7c300-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="7c300-118">Implementacja elementu członkowskiego interfejsu jawnego jest zapisywana przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c300-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="7c300-119">Na przykład `EditBox` klasa może `IControl.Paint` implementować i `IDataBound.Bind` metody przy użyciu implementacji elementu członkowskiego interfejsu jawnego w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="7c300-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="7c300-120">Elementy członkowskie interfejsu jawne są dostępne tylko za pośrednictwem typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c300-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="7c300-121">Na przykład implementacji `IControl.Paint` dostarczonych przez poprzednią klasę EditBox można wywołać tylko przez pierwsze konwertowanie `EditBox` odwołania do typu `IControl` interfejsu.</span><span class="sxs-lookup"><span data-stu-id="7c300-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="7c300-122">[Poprzedni](arrays.md)
>[następny](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="7c300-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>
