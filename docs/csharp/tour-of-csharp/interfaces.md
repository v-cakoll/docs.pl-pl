---
title: C#Interfejsy — Przewodnik po C# języku
description: Interfejsy definiują kontrakty zaimplementowane przez typy wC#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: d10d9f69cebe9a05cdff9b9ff5d817237bf8c56f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346837"
---
# <a name="interfaces"></a><span data-ttu-id="d8880-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="d8880-103">Interfaces</span></span>

<span data-ttu-id="d8880-104">***Interfejs*** definiuje kontrakt, który może być zaimplementowany przez klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="d8880-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="d8880-105">Interfejs może zawierać metody, właściwości, zdarzenia i indeksatory.</span><span class="sxs-lookup"><span data-stu-id="d8880-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="d8880-106">Interfejs nie dostarcza implementacji elementów członkowskich, które definiuje — tylko określa elementy członkowskie, które muszą być dostarczone przez klasy lub struktury, które implementują interfejs.</span><span class="sxs-lookup"><span data-stu-id="d8880-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="d8880-107">Interfejsy mogą wykorzystywać ***wielokrotne dziedziczenie***.</span><span class="sxs-lookup"><span data-stu-id="d8880-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="d8880-108">W poniższym przykładzie interfejs `IComboBox` dziedziczy po obu `ITextBox` i `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="d8880-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="d8880-109">Klasy i struktury mogą implementować wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="d8880-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="d8880-110">W poniższym przykładzie Klasa `EditBox` implementuje obu `IControl` i `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="d8880-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="d8880-111">Gdy Klasa lub struktura implementuje określony interfejs, wystąpienia tej klasy lub struktury mogą być niejawnie konwertowane na typ tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d8880-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="d8880-112">Na przykład</span><span class="sxs-lookup"><span data-stu-id="d8880-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="d8880-113">W przypadkach, gdy wystąpienie nie jest statycznie znane do implementacji określonego interfejsu, można użyć rzutowania typu dynamicznego.</span><span class="sxs-lookup"><span data-stu-id="d8880-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="d8880-114">Na przykład następujące instrukcje używają rzutowania typu dynamicznego do uzyskiwania `IControl` i implementacji interfejsu `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="d8880-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="d8880-115">Ponieważ rzeczywisty typ obiektu jest `EditBox`, rzutowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="d8880-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="d8880-116">W poprzedniej klasie `EditBox` Metoda `Paint` z interfejsu `IControl` oraz Metoda `Bind` z interfejsu `IDataBound` są implementowane przy użyciu publicznych członków.</span><span class="sxs-lookup"><span data-stu-id="d8880-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="d8880-117">C#obsługuje również jawne ***implementacje elementu członkowskiego interfejsu***, co pozwala klasie lub strukturze uniknąć udostępniania elementów członkowskich publicznie.</span><span class="sxs-lookup"><span data-stu-id="d8880-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="d8880-118">Implementacja jawnego elementu członkowskiego interfejsu jest zapisywana przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d8880-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="d8880-119">Na przykład Klasa `EditBox` może zaimplementować metody `IControl.Paint` i `IDataBound.Bind` przy użyciu jawnych implementacji elementu członkowskiego interfejsu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="d8880-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="d8880-120">Dostęp do jawnych elementów członkowskich interfejsu można uzyskać tylko za pośrednictwem typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="d8880-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="d8880-121">Na przykład implementacja `IControl.Paint` dostarczonej przez poprzednią klasę EditBox można wywołać tylko przez pierwsze przekonwertowanie odwołania `EditBox` do typu interfejsu `IControl`.</span><span class="sxs-lookup"><span data-stu-id="d8880-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
><span data-ttu-id="d8880-122">[Poprzedni](arrays.md)
>[Następny](delegates.md)</span><span class="sxs-lookup"><span data-stu-id="d8880-122">[Previous](arrays.md)
[Next](delegates.md)</span></span>
