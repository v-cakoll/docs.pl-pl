---
title: Indeksatory w interfejsach C# — Przewodnik programowania
ms.date: 02/08/2020
helpviewer_keywords:
- indexers [C#], in interfaces
- accessors [C#], indexers
ms.assetid: e16b54bd-4a83-4f52-bd75-65819fca79e8
ms.openlocfilehash: 667a4213626ee37bfc5bf8c4fe78c2cf7186a73e
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77627841"
---
# <a name="indexers-in-interfaces-c-programming-guide"></a><span data-ttu-id="5ba55-102">Indeksatory w interfejsach (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="5ba55-102">Indexers in Interfaces (C# Programming Guide)</span></span>

<span data-ttu-id="5ba55-103">Indeksatory mogą być deklarowane w [interfejsie](../../language-reference/keywords/interface.md).</span><span class="sxs-lookup"><span data-stu-id="5ba55-103">Indexers can be declared on an [interface](../../language-reference/keywords/interface.md).</span></span> <span data-ttu-id="5ba55-104">Metody dostępu indeksatorów interfejsów różnią się od metod dostępu indeksatorów [klas](../../language-reference/keywords/class.md) w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="5ba55-104">Accessors of interface indexers differ from the accessors of [class](../../language-reference/keywords/class.md) indexers in the following ways:</span></span>

- <span data-ttu-id="5ba55-105">Metody dostępu interfejsów nie używają modyfikatorów.</span><span class="sxs-lookup"><span data-stu-id="5ba55-105">Interface accessors do not use modifiers.</span></span>
- <span data-ttu-id="5ba55-106">Metoda dostępu do interfejsu zazwyczaj nie ma treści.</span><span class="sxs-lookup"><span data-stu-id="5ba55-106">An interface accessor typically does not have a body.</span></span>

<span data-ttu-id="5ba55-107">Celem metody dostępu jest wskazanie, czy indeksator jest tylko do odczytu i zapisu, tylko do odczytu lub tylko do zapisu.</span><span class="sxs-lookup"><span data-stu-id="5ba55-107">The purpose of the accessor is to indicate whether the indexer is read-write, read-only, or write-only.</span></span> <span data-ttu-id="5ba55-108">Możesz podać implementację indeksatora zdefiniowanego w interfejsie, ale jest to rzadkie.</span><span class="sxs-lookup"><span data-stu-id="5ba55-108">You may provide an implementation for an indexer defined in an interface, but this is rare.</span></span> <span data-ttu-id="5ba55-109">Indeksatory zwykle definiują interfejs API do uzyskiwania dostępu do pól danych, a pola danych nie mogą być zdefiniowane w interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5ba55-109">Indexers typically define an API to access data fields, and data fields cannot be defined in an interface.</span></span>

<span data-ttu-id="5ba55-110">Oto przykład metody dostępu indeksatora interfejsu:</span><span class="sxs-lookup"><span data-stu-id="5ba55-110">The following is an example of an interface indexer accessor:</span></span>

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#DefineIndexer)]

<span data-ttu-id="5ba55-111">Podpis indeksatora musi różnić się od sygnatur wszystkich innych indeksatorów zadeklarowanych w tym samym interfejsie.</span><span class="sxs-lookup"><span data-stu-id="5ba55-111">The signature of an indexer must differ from the signatures of all other indexers declared in the same interface.</span></span>

## <a name="example"></a><span data-ttu-id="5ba55-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="5ba55-112">Example</span></span>

<span data-ttu-id="5ba55-113">Poniższy przykład pokazuje, jak zaimplementować indeksatory interfejsów.</span><span class="sxs-lookup"><span data-stu-id="5ba55-113">The following example shows how to implement interface indexers.</span></span>

[!code-csharp[Implement](~/samples/snippets/csharp/interfaces/indexers.cs#ImplementInterface)]

[!code-csharp[DefineInterface](~/samples/snippets/csharp/interfaces/indexers.cs#ExampleCode)]

<span data-ttu-id="5ba55-114">W powyższym przykładzie można użyć jawnej implementacji elementu członkowskiego interfejsu przy użyciu w pełni kwalifikowanej nazwy elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5ba55-114">In the preceding example, you could use the explicit interface member implementation by using the fully qualified name of the interface member.</span></span> <span data-ttu-id="5ba55-115">Na przykład</span><span class="sxs-lookup"><span data-stu-id="5ba55-115">For example</span></span>

```csharp
string IIndexInterface.this[int index]
{
}
```

<span data-ttu-id="5ba55-116">Jednak w pełni kwalifikowana nazwa jest wymagana tylko wtedy, gdy klasa implementuje więcej niż jeden interfejs o tej samej sygnaturze indeksatora.</span><span class="sxs-lookup"><span data-stu-id="5ba55-116">However, the fully qualified name is only needed to avoid ambiguity when the class is implementing more than one interface with the same indexer signature.</span></span> <span data-ttu-id="5ba55-117">Na przykład jeśli Klasa `Employee` implementuje dwa interfejsy, `ICitizen` i `IEmployee`, a oba interfejsy mają ten sam podpis indeksatora, wymagana jest Jawna implementacja elementu członkowskiego interfejsu.</span><span class="sxs-lookup"><span data-stu-id="5ba55-117">For example, if an `Employee` class is implementing two interfaces, `ICitizen` and `IEmployee`, and both interfaces have the same indexer signature, the explicit interface member implementation is necessary.</span></span> <span data-ttu-id="5ba55-118">Oznacza to, że następująca deklaracja indeksatora:</span><span class="sxs-lookup"><span data-stu-id="5ba55-118">That is, the following indexer declaration:</span></span>

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

<span data-ttu-id="5ba55-119">implementuje indeksator w interfejsie `ICitizen`.</span><span class="sxs-lookup"><span data-stu-id="5ba55-119">implements the indexer on the `ICitizen` interface.</span></span>

## <a name="see-also"></a><span data-ttu-id="5ba55-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5ba55-120">See also</span></span>

- [<span data-ttu-id="5ba55-121">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5ba55-121">C# Programming Guide</span></span>](../index.md)
- <span data-ttu-id="5ba55-122">[Indexers](./index.md) (Indeksatory)</span><span class="sxs-lookup"><span data-stu-id="5ba55-122">[Indexers](./index.md)</span></span>
- [<span data-ttu-id="5ba55-123">Właściwości</span><span class="sxs-lookup"><span data-stu-id="5ba55-123">Properties</span></span>](../classes-and-structs/properties.md)
- [<span data-ttu-id="5ba55-124">Interfejsy</span><span class="sxs-lookup"><span data-stu-id="5ba55-124">Interfaces</span></span>](../interfaces/index.md)
