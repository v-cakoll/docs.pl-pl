---
title: C# atrybutów — samouczek języka C#
description: Dowiedz się więcej o deklaratywne programowania w języku C# przy użyciu atrybutów
keywords: .NET, języka csharp
author: BillWagner
ms.author: wiwagn
ms.date: 08/10/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 753bcfe2-7ddd-4487-9513-ba70937fc8e9
ms.openlocfilehash: 6878a408ef892ee47a03bfa04f736b9bf9671696
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/21/2017
---
# <a name="attributes"></a><span data-ttu-id="e283c-104">Atrybuty</span><span class="sxs-lookup"><span data-stu-id="e283c-104">Attributes</span></span>

<span data-ttu-id="e283c-105">Typy elementów członkowskich i inne jednostki w programie C# obsługuje modyfikatory, które kontrolować niektóre aspekty ich zachowanie.</span><span class="sxs-lookup"><span data-stu-id="e283c-105">Types, members, and other entities in a C# program support modifiers that control certain aspects of their behavior.</span></span> <span data-ttu-id="e283c-106">Na przykład dostępność metody jest kontrolowany przy użyciu `public`, `protected`, `internal`, i `private` modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="e283c-106">For example, the accessibility of a method is controlled using the `public`, `protected`, `internal`, and `private` modifiers.</span></span> <span data-ttu-id="e283c-107">C# uogólnia tę możliwość w taki sposób, że typy zdefiniowane przez użytkownika informacji, deklaratywne może być dołączony do programu jednostek i pobierane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e283c-107">C# generalizes this capability such that user-defined types of declarative information can be attached to program entities and retrieved at run-time.</span></span> <span data-ttu-id="e283c-108">Programy Określ dodatkowe informacje deklaratywne przez definiowanie i użycie ***atrybutów***.</span><span class="sxs-lookup"><span data-stu-id="e283c-108">Programs specify this additional declarative information by defining and using ***attributes***.</span></span>

<span data-ttu-id="e283c-109">Poniższy przykład deklaruje `HelpAttribute` atrybut, który można umieścić na jednostkach program zapewnienie linki do dokumentacji skojarzone.</span><span class="sxs-lookup"><span data-stu-id="e283c-109">The following example declares a `HelpAttribute` attribute that can be placed on program entities to provide links to their associated documentation.</span></span>

[!code-csharp[AttributeDefined](../../../samples/snippets/csharp/tour/attributes/Program.cs#L3-L20)]

<span data-ttu-id="e283c-110">Wszystkie klasy atrybutu pochodzi od <xref:System.Attribute> pochodzącymi z biblioteki standardowej klasy podstawowej.</span><span class="sxs-lookup"><span data-stu-id="e283c-110">All attribute classes derive from the <xref:System.Attribute> base class provided by the standard library.</span></span> <span data-ttu-id="e283c-111">Atrybuty można zastosować, zapewniając ich nazw, wraz z żadnych argumentów w nawiasach kwadratowych bezpośrednio przed deklaracją skojarzone.</span><span class="sxs-lookup"><span data-stu-id="e283c-111">Attributes can be applied by giving their name, along with any arguments, inside square brackets just before the associated declaration.</span></span> <span data-ttu-id="e283c-112">Jeśli nazwa atrybutu kończy się `Attribute`, gdy odwołuje się do atrybutu można pominąć części nazwy.</span><span class="sxs-lookup"><span data-stu-id="e283c-112">If an attribute’s name ends in `Attribute`, that part of the name can be omitted when the attribute is referenced.</span></span> <span data-ttu-id="e283c-113">Na przykład `HelpAttribute` atrybut może być używany w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="e283c-113">For example, the `HelpAttribute` attribute can be used as follows.</span></span>

[!code-csharp[AttributeApplied](../../../samples/snippets/csharp/tour/attributes/Program.cs#L22-L28)]

<span data-ttu-id="e283c-114">W tym przykładzie dołącza `HelpAttribute` do `Widget` klasy.</span><span class="sxs-lookup"><span data-stu-id="e283c-114">This example attaches a `HelpAttribute` to the `Widget` class.</span></span> <span data-ttu-id="e283c-115">Dodaje innego `HelpAttribute` do `Display` metody w klasie.</span><span class="sxs-lookup"><span data-stu-id="e283c-115">It adds another `HelpAttribute` to the `Display` method in the class.</span></span> <span data-ttu-id="e283c-116">Konstruktory publiczne klasy atrybutu kontrolować informacje, które należy podać, gdy atrybut jest dołączony do jednostki programu.</span><span class="sxs-lookup"><span data-stu-id="e283c-116">The public constructors of an attribute class control the information that must be provided when the attribute is attached to a program entity.</span></span> <span data-ttu-id="e283c-117">Dodatkowe informacje może być udostępniane przez publicznego właściwości odczytu / zapisu z klasy atrybutów odwołania (np. odwołanie do `Topic` właściwości wcześniej).</span><span class="sxs-lookup"><span data-stu-id="e283c-117">Additional information can be provided by referencing public read-write properties of the attribute class (such as the reference to the `Topic` property previously).</span></span>

<span data-ttu-id="e283c-118">Określonego atrybutu zleconą przez odbicie konstruktora dla klasy atrybutów jest wywoływana z informacji dostępnych w źródle programu, a wynikowy wystąpienie atrybutu jest zwracane.</span><span class="sxs-lookup"><span data-stu-id="e283c-118">When a particular attribute is requested through reflection, the constructor for the attribute class is invoked with the information provided in the program source, and the resulting attribute instance is returned.</span></span> <span data-ttu-id="e283c-119">Jeśli dodatkowe informacje były udostępniane za pośrednictwem właściwości, te właściwości są ustawione na wartości danego przed zwróceniem wystąpienie atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e283c-119">If additional information was provided through properties, those properties are set to the given values before the attribute instance is returned.</span></span>

>[!div class="step-by-step"]
[<span data-ttu-id="e283c-120">Poprzednie</span><span class="sxs-lookup"><span data-stu-id="e283c-120">Previous</span></span>](delegates.md)
