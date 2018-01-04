---
title: "Wyliczanie ciągów formatujących"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- format specifiers, enumeration format strings
- enumeration format strings
- formatting [.NET Framework], enumeration
ms.assetid: dd1ff672-1052-42cf-8666-4924fb6cd1a1
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 58004fa19f2ec3b1ca7570d6ca75702510148002
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="enumeration-format-strings"></a><span data-ttu-id="a5f74-102">Wyliczanie ciągów formatujących</span><span class="sxs-lookup"><span data-stu-id="a5f74-102">Enumeration Format Strings</span></span>
<span data-ttu-id="a5f74-103">Można użyć <xref:System.Enum.ToString%2A?displayProperty=nameWithType> metodę, aby utworzyć nowy obiekt ciągu reprezentujący liczbowe, szesnastkowo lub wartość ciągu dla elementu członkowskiego wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="a5f74-103">You can use the <xref:System.Enum.ToString%2A?displayProperty=nameWithType> method to create a new string object that represents the numeric, hexadecimal, or string value of an enumeration member.</span></span> <span data-ttu-id="a5f74-104">Ta metoda przyjmuje jeden wyliczenie formatowania ciągi, aby określić wartości, które mają być zwracane.</span><span class="sxs-lookup"><span data-stu-id="a5f74-104">This method takes one of the enumeration formatting strings to specify the value that you want returned.</span></span>  
  
 <span data-ttu-id="a5f74-105">W poniższej tabeli wymieniono wyliczenie formatowanie ciągów i wartości, które zwracają.</span><span class="sxs-lookup"><span data-stu-id="a5f74-105">The following table lists the enumeration formatting strings and the values they return.</span></span> <span data-ttu-id="a5f74-106">Te specyfikatory formatu nie jest rozróżniana.</span><span class="sxs-lookup"><span data-stu-id="a5f74-106">These format specifiers are not case-sensitive.</span></span>  
  
| <span data-ttu-id="a5f74-107">Ciąg formatu</span><span class="sxs-lookup"><span data-stu-id="a5f74-107">Format string</span></span> | <span data-ttu-id="a5f74-108">Wynik</span><span class="sxs-lookup"><span data-stu-id="a5f74-108">Result</span></span> |  
| ------------- | ------ |  
| <span data-ttu-id="a5f74-109">G lub g</span><span class="sxs-lookup"><span data-stu-id="a5f74-109">G or g</span></span> | <span data-ttu-id="a5f74-110">Wyświetla wpis wyliczenie jako wartość typu ciąg, jeśli to możliwe, a w przeciwnym razie wyświetlana jest wartość całkowitą bieżącego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a5f74-110">Displays the enumeration entry as a string value, if possible, and otherwise displays the integer value of the current instance.</span></span> <span data-ttu-id="a5f74-111">Jeśli zdefiniowano wyliczenia z **flagi** ustawiony atrybut, ciąg wartości każdy nieprawidłowy wpis są połączone ze sobą, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a5f74-111">If the enumeration is defined with the **Flags** attribute set, the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="a5f74-112">Jeśli **flagi** atrybut nie jest ustawiony, nieprawidłową wartość jest wyświetlana jako wpis liczbowych.</span><span class="sxs-lookup"><span data-stu-id="a5f74-112">If the **Flags** attribute is not set, an invalid value is displayed as a numeric entry.</span></span> <span data-ttu-id="a5f74-113">Poniższy przykład przedstawia specyfikator formatu G.</span><span class="sxs-lookup"><span data-stu-id="a5f74-113">The following example illustrates the G format specifier.</span></span><br><br><span data-ttu-id="a5f74-114">[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="a5f74-114">[!code-csharp[Formatting.Enum#1](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#1)] [!code-vb[Formatting.Enum#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#1)]</span></span> |  
| <span data-ttu-id="a5f74-115">F lub f</span><span class="sxs-lookup"><span data-stu-id="a5f74-115">F or f</span></span> | <span data-ttu-id="a5f74-116">Wyświetla wyliczenie hasło w postaci wartości ciągu, jeśli to możliwe.</span><span class="sxs-lookup"><span data-stu-id="a5f74-116">Displays the enumeration entry as a string value, if possible.</span></span> <span data-ttu-id="a5f74-117">Jeśli wartość, które mogą być całkowicie wyświetlane jako suma wpisów w wyliczeniu (nawet jeśli **flagi** atrybut nie jest obecny), wartości ciągu każdego wpisu prawidłowe są łączone, oddzielonych przecinkami.</span><span class="sxs-lookup"><span data-stu-id="a5f74-117">If the value can be completely displayed as a summation of the entries in the enumeration (even if the **Flags** attribute is not present), the string values of each valid entry are concatenated together, separated by commas.</span></span> <span data-ttu-id="a5f74-118">Jeśli wartość nie może całkowicie określana na podstawie pozycji wyliczenia, wartość jest formatowana jako wartość całkowita.</span><span class="sxs-lookup"><span data-stu-id="a5f74-118">If the value cannot be completely determined by the enumeration entries, then the value is formatted as the integer value.</span></span> <span data-ttu-id="a5f74-119">Poniższy przykład przedstawia specyfikator formatu F.</span><span class="sxs-lookup"><span data-stu-id="a5f74-119">The following example illustrates the F format specifier.</span></span><br><br><span data-ttu-id="a5f74-120">[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="a5f74-120">[!code-csharp[Formatting.Enum#2](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#2)] [!code-vb[Formatting.Enum#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#2)]</span></span> |  
| <span data-ttu-id="a5f74-121">D lub d</span><span class="sxs-lookup"><span data-stu-id="a5f74-121">D or d</span></span> | <span data-ttu-id="a5f74-122">Wyświetla wpis wyliczenie jako wartość całkowitą w możliwie najkrótszym reprezentacji możliwe.</span><span class="sxs-lookup"><span data-stu-id="a5f74-122">Displays the enumeration entry as an integer value in the shortest representation possible.</span></span> <span data-ttu-id="a5f74-123">Poniższy przykład przedstawia specyfikator formatu D.</span><span class="sxs-lookup"><span data-stu-id="a5f74-123">The following example illustrates the D format specifier.</span></span><br><br><span data-ttu-id="a5f74-124">[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="a5f74-124">[!code-csharp[Formatting.Enum#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#3)] [!code-vb[Formatting.Enum#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#3)]</span></span> |  
| <span data-ttu-id="a5f74-125">X lub x</span><span class="sxs-lookup"><span data-stu-id="a5f74-125">X or x</span></span> | <span data-ttu-id="a5f74-126">Wyświetla wpis wyliczenie jako wartość szesnastkową.</span><span class="sxs-lookup"><span data-stu-id="a5f74-126">Displays the enumeration entry as a hexadecimal value.</span></span> <span data-ttu-id="a5f74-127">Wartość jest reprezentowany z zerami w razie potrzeby do zapewnienia, że wartość minimalna ośmiu cyfr długości.</span><span class="sxs-lookup"><span data-stu-id="a5f74-127">The value is represented with leading zeros as necessary, to ensure that the value is a minimum eight digits in length.</span></span> <span data-ttu-id="a5f74-128">Poniższy przykład przedstawia specyfikator formatu X.</span><span class="sxs-lookup"><span data-stu-id="a5f74-128">The following example illustrates the X format specifier.</span></span><br /><br /> <span data-ttu-id="a5f74-129">[!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span><span class="sxs-lookup"><span data-stu-id="a5f74-129">[!code-csharp[Formatting.Enum#4](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#4)] [!code-vb[Formatting.Enum#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#4)]</span></span> |  
  
## <a name="example"></a><span data-ttu-id="a5f74-130">Przykład</span><span class="sxs-lookup"><span data-stu-id="a5f74-130">Example</span></span>  
 <span data-ttu-id="a5f74-131">W poniższym przykładzie zdefiniowano wyliczenie o nazwie `Colors` składający się z trzech wpisów: `Red`, `Blue`, i `Green`.</span><span class="sxs-lookup"><span data-stu-id="a5f74-131">The following example defines an enumeration called `Colors` that consists of three entries: `Red`, `Blue`, and `Green`.</span></span>  
  
 [!code-csharp[Formatting.Enum#5](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#5)]
 [!code-vb[Formatting.Enum#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#5)]  
  
 <span data-ttu-id="a5f74-132">Po zdefiniowaniu wyliczenia wystąpienia mogą być deklarowane w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="a5f74-132">After the enumeration is defined, an instance can be declared in the following manner.</span></span>  
  
 [!code-csharp[Formatting.Enum#6](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#6)]
 [!code-vb[Formatting.Enum#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#6)]  
  
 <span data-ttu-id="a5f74-133">`Color.ToString(System.String)` Metody następnie może służyć do wyświetlania wartości wyliczenia na różne sposoby, w zależności od specyfikator formatu przekazany do niego.</span><span class="sxs-lookup"><span data-stu-id="a5f74-133">The `Color.ToString(System.String)` method can then be used to display the enumeration value in different ways, depending on the format specifier passed to it.</span></span>  
  
 [!code-csharp[Formatting.Enum#7](../../../samples/snippets/csharp/VS_Snippets_CLR/Formatting.Enum/cs/enum1.cs#7)]
 [!code-vb[Formatting.Enum#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Formatting.Enum/vb/enum1.vb#7)]  
  
## <a name="see-also"></a><span data-ttu-id="a5f74-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a5f74-134">See Also</span></span>  
 [<span data-ttu-id="a5f74-135">Formatowanie typów</span><span class="sxs-lookup"><span data-stu-id="a5f74-135">Formatting Types</span></span>](../../../docs/standard/base-types/formatting-types.md)
