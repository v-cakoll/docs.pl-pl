---
title: Indeksatory w interfejsach — przewodnik programowania C#
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627841"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="1ffdb-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="1ffdb-103">Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="1ffdb-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="1ffdb-104">Akcesory indeksatorów interfejsu różnią się od akcesorów indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1ffdb-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="1ffdb-105">Akcesory interfejsu nie używają modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="1ffdb-106">Akcesor interfejsu zazwyczaj nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="1ffdb-107">Celem akcesora jest wskazanie, czy indeksator jest zapisu do odczytu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="1ffdb-108">Można podać implementację dla indeksatora zdefiniowane w interfejsie, ale jest to rzadkie.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="1ffdb-109">Indeksatory zazwyczaj definiują interfejs API, aby uzyskać dostęp do pól danych, a pola danych nie mogą być zdefiniowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="1ffdb-110">Poniżej przedstawiono przykład akcesora indeksatora interfejsu:</span><span class="sxs-lookup"><span data-stu-id="1ffdb-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="1ffdb-111">Podpis indeksatora musi różnić się od podpisów wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="1ffdb-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ffdb-112">Example</span></span>

<span data-ttu-id="1ffdb-113">W poniższym przykładzie pokazano, jak zaimplementować indeksatory interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="1ffdb-114">W poprzednim przykładzie można użyć implementacji elementu członkowskiego interfejsu jawnego przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="1ffdb-115">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1ffdb-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="1ffdb-116">Jednak w pełni kwalifikowana nazwa jest potrzebna tylko w celu uniknięcia niejednoznaczności, gdy klasa implementuje więcej niż jeden interfejs z tym samym podpisem indeksatora.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="1ffdb-117">Na przykład jeśli `Employee` klasa implementuje dwa `ICitizen` `IEmployee`interfejsy i , i oba interfejsy mają ten sam podpis indeksatora, implementacja elementu członkowskiego interfejsu jawnego jest konieczne.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="1ffdb-118">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="1ffdb-118">That is, the following indexer declaration:</span></span>

```csharp
string IEmployee.this[int index]
{
}
``

implements the indexer on the `IEmployee` interface, while the following declaration:

```csharp
string ICitizen.this[int index]
{
}
```

<span data-ttu-id="1ffdb-119">implementuje indeksatora `ICitizen` w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="1ffdb-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="1ffdb-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ffdb-120">See also</span></span>

- [<span data-ttu-id="1ffdb-121">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="1ffdb-121">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="1ffdb-122">[Indexers](./index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="1ffdb-122">[Indexers](./index.md)</span></span>
- [<span data-ttu-id="1ffdb-123">Właściwości</span><span class="sxs-lookup"><span data-stu-id="1ffdb-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="1ffdb-124">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="1ffdb-124">Interfaces</span></span>](../interfaces/index.md)
