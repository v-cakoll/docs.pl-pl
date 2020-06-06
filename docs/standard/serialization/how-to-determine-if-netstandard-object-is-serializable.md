---
title: Jak ustalić, czy obiekt .NET Standard jest możliwy do serializacji
description: Pokazuje, jak ustalić, czy typ .NET Standard może być serializowany w czasie wykonywania.
ms.date: 10/20/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
ms.openlocfilehash: b6791ae0666aeb0ac02d8a38ca419d7de2b263cf
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "84289606"
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="ee7ad-103">Jak ustalić, czy obiekt .NET Standard jest możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="ee7ad-103">How to determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="ee7ad-104">.NET Standard to specyfikacja, która definiuje typy i elementy członkowskie, które muszą być obecne w określonych implementacjach platformy .NET, które są zgodne z tą wersją Standard.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="ee7ad-105">Jednak .NET Standard nie definiuje, czy typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="ee7ad-106">Typy zdefiniowane w bibliotece .NET Standard nie są oznaczone <xref:System.SerializableAttribute> atrybutem.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="ee7ad-107">Zamiast tego konkretne implementacje platformy .NET, takie jak .NET Framework i .NET Core, są bezpłatne, aby określić, czy dany typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span>

<span data-ttu-id="ee7ad-108">Jeśli opracowano bibliotekę, która jest przeznaczona dla .NET Standard, biblioteka może być używana przez dowolną implementację platformy .NET, która obsługuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="ee7ad-109">Oznacza to, że nie można wcześniej sprawdzić, czy dany typ jest możliwy do serializacji; można określić tylko, czy ma on być możliwy do serializacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="ee7ad-110">Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania przez pobranie wartości <xref:System.Type.IsSerializable> właściwości <xref:System.Type> obiektu, który reprezentuje typ tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-110">You can determine whether an object is serializable at run time by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="ee7ad-111">Poniższy przykład zawiera jedną implementację.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-111">The following example provides one implementation.</span></span> <span data-ttu-id="ee7ad-112">Definiuje `IsSerializable(Object)` metodę rozszerzenia, która wskazuje, czy dowolne <xref:System.Object> wystąpienie może być serializowane.</span><span class="sxs-lookup"><span data-stu-id="ee7ad-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="ee7ad-113">Następnie można przekazać dowolny obiekt do metody, aby określić, czy można serializować i zdeserializować w bieżącej implementacji platformy .NET, jak pokazano na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="ee7ad-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

## <a name="see-also"></a><span data-ttu-id="ee7ad-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee7ad-114">See also</span></span>

- [<span data-ttu-id="ee7ad-115">Serializacja binarna</span><span class="sxs-lookup"><span data-stu-id="ee7ad-115">Binary serialization</span></span>](binary-serialization.md)
- <xref:System.SerializableAttribute?displayProperty=nameWithType>
- <xref:System.Type.IsSerializable?displayProperty=nameWithType>
