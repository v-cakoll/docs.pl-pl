---
title: C#Interfejsy — Przewodnik po przykładzie C# języka
description: Interfejsy definiują kontraktów implementowany przez typy wC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: bfc6b59a411ff2ddb3331a8bdf24c0ae3d611273
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61706406"
---
# <a name="interfaces"></a><span data-ttu-id="89bc0-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="89bc0-103">Interfaces</span></span>

<span data-ttu-id="89bc0-104">***Interfejsu*** definiuje kontrakt, który może być implementowany przez klas i struktur.</span><span class="sxs-lookup"><span data-stu-id="89bc0-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="89bc0-105">Interfejs może zawierać metody, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="89bc0-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="89bc0-106">Interfejs nie zawiera implementacji członków definiuje — jedynie określa elementy członkowskie, które muszą być dostarczane przez klasy lub struktury, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="89bc0-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="89bc0-107">Interfejsy mogą stosować ***wielokrotne dziedziczenie***.</span><span class="sxs-lookup"><span data-stu-id="89bc0-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="89bc0-108">W poniższym przykładzie interfejs `IComboBox` dziedziczy z obu `ITextBox` i `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="89bc0-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="89bc0-109">Klasy i struktury można zaimplementować wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="89bc0-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="89bc0-110">W poniższym przykładzie klasa `EditBox` implementuje interfejsy `IControl` i `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="89bc0-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="89bc0-111">Gdy klasa lub struktura implementuje danego interfejsu, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane do tego typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="89bc0-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="89bc0-112">Na przykład</span><span class="sxs-lookup"><span data-stu-id="89bc0-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="89bc0-113">W przypadkach, gdy wystąpienie nie jest znany statycznie do implementowania określonego interfejsu służy rzutowania typu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="89bc0-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="89bc0-114">Na przykład poniższe instrukcje użyć rzutowania typu dynamicznego do uzyskiwania obiektu `IControl` i `IDataBound` implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="89bc0-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="89bc0-115">Ponieważ jest środowiska wykonawczego, rzeczywisty typ obiektu `EditBox`, rzutowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="89bc0-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="89bc0-116">W ciągu poprzednich `EditBox` klasy `Paint` metody z `IControl` interfejsu i `Bind` metody z `IDataBound` interfejsu są implementowane przy użyciu publicznych składowych.</span><span class="sxs-lookup"><span data-stu-id="89bc0-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="89bc0-117">C#również obsługuje jawnej ***interfejsu implementacji elementu członkowskiego***, umożliwiając klasy lub struktury, aby uniknąć konieczności publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="89bc0-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="89bc0-118">Implementacja interfejsu jawnego członka jest zapisywany przy użyciu interfejsu w pełni kwalifikowana nazwa elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="89bc0-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="89bc0-119">Na przykład `EditBox` implementacji klasy `IControl.Paint` i `IDataBound.Bind` metod za pomocą jawnych implementacji elementu członkowskiego interfejsu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="89bc0-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="89bc0-120">Elementy członkowskie interfejsu jawnego zostać oceniony jedynie przez typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="89bc0-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="89bc0-121">Na przykład implementacji `IControl.Paint` dostarczone przez poprzednie EditBox klasy może być wywoływany tylko przez uprzedniego przekonwertowania `EditBox` odwołanie do `IControl` typ interfejsu.</span><span class="sxs-lookup"><span data-stu-id="89bc0-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="89bc0-122">[Poprzednie](arrays.md)
>[dalej](enums.md)</span><span class="sxs-lookup"><span data-stu-id="89bc0-122">[Previous](arrays.md)
[Next](enums.md)</span></span>