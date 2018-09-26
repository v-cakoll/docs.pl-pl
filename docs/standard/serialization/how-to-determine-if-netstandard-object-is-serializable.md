---
title: Jak ustalić, czy obiekt standardowy .NET jest możliwy do serializacji
description: Pokazuje, jak ustalić, czy typ .NET Standard może być serializowany w czasie wykonywania.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 196e99ab1f1a0baae53c6a1dc295b135e36fbfe0
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080276"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="71105-103">Jak ustalić, czy obiekt standardowy .NET jest możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="71105-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="71105-104">.NET Standard to specyfikacja, która definiuje typy i elementy członkowskie, które musi znajdować się na określonej implementacji platformy .NET, które są zgodne z wersji standard.</span><span class="sxs-lookup"><span data-stu-id="71105-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="71105-105">Jednak .NET Standard nie definiuje czy typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="71105-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="71105-106">Typy zdefiniowane w standardowej bibliotece platformy .NET nie są oznaczone <xref:System.SerializableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="71105-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="71105-107">Zamiast tego określonej implementacji platformy .NET, takich jak .NET Framework i .NET Core mogą swobodnie ustalać, czy określony typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="71105-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="71105-108">Tworzyli biblioteki .NET Standard przeznaczonego, biblioteki mogą być używane przez wszystkie implementacji .NET, która obsługuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="71105-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="71105-109">Oznacza to, że możesz nie wiedzieć z wyprzedzeniem czy określonego typu jest możliwy do serializacji; należy tylko określić, czy jest możliwy do serializacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="71105-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="71105-110">Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania, poprzez pobranie wartości <xref:System.Type.IsSerializable> właściwość <xref:System.Type> obiektu, który reprezentuje typ tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="71105-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="71105-111">W poniższym przykładzie przedstawiono jedna implementacja.</span><span class="sxs-lookup"><span data-stu-id="71105-111">The following example provides one implementation.</span></span> <span data-ttu-id="71105-112">Definiuje on `IsSerializable(Object)` metodę rozszerzenia, która wskazuje, czy którekolwiek <xref:System.Object> wystąpienia może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="71105-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="71105-113">Dowolny obiekt można następnie przekazać do metody w celu określenia, czy może być serializacji i deserializacji bieżącej implementacji .NET, co ilustruje poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="71105-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="71105-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="71105-114">See also</span></span>

- [<span data-ttu-id="71105-115">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="71105-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
