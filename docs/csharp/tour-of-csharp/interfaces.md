---
title: Interfejsy języka C# — samouczek języka C#
description: Interfejsy Definiowanie kontraktów zaimplementowanych przez typy w języku C#
ms.date: 08/10/2016
ms.assetid: a9bf82f4-efd1-4216-bd34-4ef0fa48c968
ms.openlocfilehash: 0ad02d5b2792656783d93b2cc767aeb81efbc30e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33343899"
---
# <a name="interfaces"></a><span data-ttu-id="67642-103">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="67642-103">Interfaces</span></span>

<span data-ttu-id="67642-104">***Interfejsu*** definiuje kontrakt może być zaimplementowany przez klasy i struktury.</span><span class="sxs-lookup"><span data-stu-id="67642-104">An ***interface*** defines a contract that can be implemented by classes and structs.</span></span> <span data-ttu-id="67642-105">Interfejs może zawierać metod, właściwości, zdarzeń i indeksatorów.</span><span class="sxs-lookup"><span data-stu-id="67642-105">An interface can contain methods, properties, events, and indexers.</span></span> <span data-ttu-id="67642-106">Interfejs nie zawiera implementacji elementów członkowskich definiuje — Określa on tylko elementy członkowskie, które muszą zostać dostarczone przez klasy lub struktury, który implementuje interfejs.</span><span class="sxs-lookup"><span data-stu-id="67642-106">An interface does not provide implementations of the members it defines—it merely specifies the members that must be supplied by classes or structs that implement the interface.</span></span>

<span data-ttu-id="67642-107">Interfejsy mogą stosować ***dziedziczenie wielokrotne***.</span><span class="sxs-lookup"><span data-stu-id="67642-107">Interfaces may employ ***multiple inheritance***.</span></span> <span data-ttu-id="67642-108">W poniższym przykładzie interfejsu `IComboBox` dziedziczy z obu `ITextBox` i `IListBox`.</span><span class="sxs-lookup"><span data-stu-id="67642-108">In the following example, the interface `IComboBox` inherits from both `ITextBox` and `IListBox`.</span></span>

[!code-csharp[InterfacesOne](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L5-L17)]

<span data-ttu-id="67642-109">Klasy i struktury można zaimplementować wiele interfejsów.</span><span class="sxs-lookup"><span data-stu-id="67642-109">Classes and structs can implement multiple interfaces.</span></span> <span data-ttu-id="67642-110">W poniższym przykładzie klasa `EditBox` implementuje zarówno `IControl` i `IDataBound`.</span><span class="sxs-lookup"><span data-stu-id="67642-110">In the following example, the class `EditBox` implements both `IControl` and `IDataBound`.</span></span>

[!code-csharp[InterfacesTwo](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L19-L27)]

<span data-ttu-id="67642-111">Po klasie lub strukturze implementuje konkretnego interfejsu, wystąpień tej klasy lub struktury można niejawnie przekonwertowana na typ tego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67642-111">When a class or struct implements a particular interface, instances of that class or struct can be implicitly converted to that interface type.</span></span> <span data-ttu-id="67642-112">Na przykład</span><span class="sxs-lookup"><span data-stu-id="67642-112">For example</span></span>

[!code-csharp[InterfacesThree](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L33-L35)]

<span data-ttu-id="67642-113">W przypadkach, gdy wystąpienie jest statycznie nieznany do zaimplementowania konkretnego interfejsu można użyć rzutowania typów dynamicznych.</span><span class="sxs-lookup"><span data-stu-id="67642-113">In cases where an instance is not statically known to implement a particular interface, dynamic type casts can be used.</span></span> <span data-ttu-id="67642-114">Na przykład następujące instrukcje umożliwia rzutowania z typu dynamicznego uzyskanie obiektu `IControl` i `IDataBound` implementacji interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67642-114">For example, the following statements use dynamic type casts to obtain an object’s `IControl` and `IDataBound` interface implementations.</span></span> <span data-ttu-id="67642-115">Ponieważ środowiska wykonawczego rzeczywisty typ obiektu to `EditBox`, rzutowania powiodło się.</span><span class="sxs-lookup"><span data-stu-id="67642-115">Because the run-time actual type of the object is `EditBox`, the casts succeed.</span></span>

[!code-csharp[InterfacesFour](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L40-L42)]

<span data-ttu-id="67642-116">W poprzednim `EditBox` klasy `Paint` metody z `IControl` interfejsu i `Bind` metody z `IDataBound` interfejsu są implementowane za pomocą publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="67642-116">In the previous `EditBox` class, the `Paint` method from the `IControl` interface and the `Bind` method from the `IDataBound` interface are implemented using public members.</span></span> <span data-ttu-id="67642-117">C# obsługuje również jawne ***implementacje elementów członkowskich interfejsu***, włączanie klasy lub struktury, aby uniknąć publiczne elementy członkowskie.</span><span class="sxs-lookup"><span data-stu-id="67642-117">C# also supports explicit ***interface member implementations***, enabling the class or struct to avoid making the members public.</span></span> <span data-ttu-id="67642-118">Implementacja interfejsu jawnego członka jest zapisywany przy użyciu interfejsu w pełni kwalifikowaną nazwę elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="67642-118">An explicit interface member implementation is written using the fully qualified interface member name.</span></span> <span data-ttu-id="67642-119">Na przykład `EditBox` można zaimplementować klasy `IControl.Paint` i `IDataBound.Bind` metody za pomocą jawnego interfejsu implementacje elementów członkowskich w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="67642-119">For example, the `EditBox` class could implement the `IControl.Paint` and `IDataBound.Bind` methods using explicit interface member implementations as follows.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L60-L64)]

<span data-ttu-id="67642-120">Elementy członkowskie interfejsu jawnego można uzyskać tylko za pośrednictwem typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67642-120">Explicit interface members can only be accessed via the interface type.</span></span> <span data-ttu-id="67642-121">Na przykład stosowania `IControl.Paint` dostarczane przez poprzednie pole edycji można wywołać tylko klasy konwertując pierwszy `EditBox` odwołanie do `IControl` typu interfejsu.</span><span class="sxs-lookup"><span data-stu-id="67642-121">For example, the implementation of `IControl.Paint` provided by the previous EditBox class can only be invoked by first converting the `EditBox` reference to the `IControl` interface type.</span></span>

[!code-csharp[InterfacesFive](../../../samples/snippets/csharp/tour/interfaces/Program.cs#L71-L74)]

>[!div class="step-by-step"]
<span data-ttu-id="67642-122">[Poprzednie](arrays.md)
[dalej](enums.md)</span><span class="sxs-lookup"><span data-stu-id="67642-122">[Previous](arrays.md)
[Next](enums.md)</span></span>
