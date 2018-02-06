---
title: "Porady: Określa, czy obiekt .NET Standard jest możliwy do serializacji"
description: "Pokazuje sposób określania, czy w czasie wykonywania można zserializować typu .NET Standard."
ms.custom: 
ms.date: 10/20/2017
ms.prod: .net
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- serializing objects
- objects, serializing steps
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 8246e825202b3eb02db5d11f1fe55b4a0d14a4ea
ms.sourcegitcommit: 099aa20d9b6450d1b7452d782a55771a6ad8ff35
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/05/2018
---
# <a name="how-to-determine-if-a-net-standard-object-is-serializable"></a><span data-ttu-id="cde10-103">Porady: Określa, czy obiekt .NET Standard jest możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="cde10-103">How to: Determine if a .NET Standard object is serializable</span></span>

<span data-ttu-id="cde10-104">.NET Standard jest specyfikacją definiujący typy i elementy członkowskie, które musi znajdować się na określonych implementacje .NET, które są zgodne z danej wersji standard.</span><span class="sxs-lookup"><span data-stu-id="cde10-104">The .NET Standard is a specification that defines the types and members that must be present on specific .NET implementations that conform to that version of the standard.</span></span> <span data-ttu-id="cde10-105">Jednak .NET Standard nie definiuje czy typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="cde10-105">However, the .NET Standard does not define whether a type is serializable.</span></span> <span data-ttu-id="cde10-106">Typów zdefiniowanych w standardowej bibliotece programu .NET nie jest oznaczony atrybutem <xref:System.SerializableAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="cde10-106">The types defined in the .NET Standard Library are not marked with the <xref:System.SerializableAttribute> attribute.</span></span> <span data-ttu-id="cde10-107">Zamiast tego określonego implementacji .NET, takich jak .NET Framework i .NET Core mogą ustalić, czy określony typ jest możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="cde10-107">Instead, specific .NET implementations, such as the .NET Framework and .NET Core, are free to determine whether a particular type is serializable.</span></span> 

<span data-ttu-id="cde10-108">Jeśli został opracowany biblioteki którego element docelowy .NET Standard, biblioteki mogą być używane przez wszystkie implementacja .NET obsługuje .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="cde10-108">If you've developed a library that targets the .NET Standard, your library can be consumed by any .NET implementation that supports the .NET Standard.</span></span> <span data-ttu-id="cde10-109">Oznacza to, że nie znasz z wyprzedzeniem czy konkretny typ jest możliwy do serializacji; można tylko określić, czy jest możliwy do serializacji w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="cde10-109">This means that you cannot know in advance whether a particular type is serializable; you can only determine whether it is serializable at run time.</span></span>

<span data-ttu-id="cde10-110">Można określić, czy obiekt jest możliwy do serializacji w czasie wykonywania, pobierając zaletą <xref:System.Type.IsSerializable> właściwość <xref:System.Type> obiekt, który reprezentuje typ tego obiektu.</span><span class="sxs-lookup"><span data-stu-id="cde10-110">You can determine whether an object is serializable at runtime by retrieving the value of the <xref:System.Type.IsSerializable> property of a <xref:System.Type> object that represents that object's type.</span></span> <span data-ttu-id="cde10-111">W poniższym przykładzie przedstawiono jeden implementacji.</span><span class="sxs-lookup"><span data-stu-id="cde10-111">The following example provides one implementation.</span></span> <span data-ttu-id="cde10-112">Definiuje `IsSerializable(Object)` — metoda rozszerzenia, która wskazuje, czy którekolwiek <xref:System.Object> wystąpienie może być Zserializowany.</span><span class="sxs-lookup"><span data-stu-id="cde10-112">It defines an `IsSerializable(Object)` extension method that indicates whether any <xref:System.Object> instance can be serialized.</span></span>

[!code-csharp[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#2)]
[!code-vb[is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/library.vb#2)]

<span data-ttu-id="cde10-113">Dowolny obiekt można następnie przekazać do metody w celu określenia, czy może być serializacji i deserializacji bieżąca implementacja .NET, jak przedstawiono na poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="cde10-113">You can then pass any object to the method to determine whether it can be serialized and deserialized on the current .NET implementation, as the following example shows:</span></span>

[!code-csharp[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/csharp/program.cs#1)]
[!code-vb[test-is-a-type-serializable](~/samples/snippets/standard/serialization/is-serializable/vb/program.vb#1)]

# <a name="see-also"></a><span data-ttu-id="cde10-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cde10-114">See also</span></span>

<span data-ttu-id="cde10-115">[Serializacja binarna](binary-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="cde10-115">[Binary serialization](binary-serialization.md) </span></span>  
<span data-ttu-id="cde10-116"><xref:System.SerializableAttribute?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="cde10-116"><xref:System.SerializableAttribute?displayProperty=nameWithType></span></span>    
<xref:System.Type.IsSerializable?displayProperty=nameWithType>   
