---
title: "Tabele konwersji typów w .NET"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- widening conversions
- narrowing conversions
- type conversion, table
- converting types, narrowing conversions
- converting types, widening conversions
- base types, converting
- tables [.NET Framework], type conversions
- data types [.NET Framework], converting
ms.assetid: 0ea65c59-85eb-4a52-94ca-c36d3bd13058
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: e741de47fec5f0ed607bba33b963d449c5c51cce
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="type-conversion-tables-in-net"></a><span data-ttu-id="d7223-102">Tabele konwersji typów w .NET</span><span class="sxs-lookup"><span data-stu-id="d7223-102">Type Conversion Tables in .NET</span></span>
<span data-ttu-id="d7223-103">Rozszerzanie konwersji występuje, gdy wartość jeden typ jest konwertowany na inny typ, który jest równy lub większy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d7223-103">Widening conversion occurs when a value of one type is converted to another type that is of equal or greater size.</span></span> <span data-ttu-id="d7223-104">Konwersji zawężającej występuje, gdy wartość jeden typ jest konwertowana na wartość innego typu, który ma mniejszy rozmiar.</span><span class="sxs-lookup"><span data-stu-id="d7223-104">A narrowing conversion occurs when a value of one type is converted to a value of another type that is of a smaller size.</span></span> <span data-ttu-id="d7223-105">Tabele w tym temacie przedstawiają zachowania eksponowane przez obu typów konwersji.</span><span class="sxs-lookup"><span data-stu-id="d7223-105">The tables in this topic illustrate the behaviors exhibited by both types of conversions.</span></span>  
  
## <a name="widening-conversions"></a><span data-ttu-id="d7223-106">Poszerzenie konwersji</span><span class="sxs-lookup"><span data-stu-id="d7223-106">Widening Conversions</span></span>  
 <span data-ttu-id="d7223-107">W poniższej tabeli opisano konwersje rozszerzającą, które mogą być wykonywane bez utraty informacji.</span><span class="sxs-lookup"><span data-stu-id="d7223-107">The following table describes the widening conversions that can be performed without the loss of information.</span></span>  
  
|<span data-ttu-id="d7223-108">Typ</span><span class="sxs-lookup"><span data-stu-id="d7223-108">Type</span></span>|<span data-ttu-id="d7223-109">Można przekonwertować bez utraty danych do</span><span class="sxs-lookup"><span data-stu-id="d7223-109">Can be converted without data loss to</span></span>|  
|----------|-------------------------------------------|  
|<xref:System.Byte>|<span data-ttu-id="d7223-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-110"><xref:System.UInt16>, <xref:System.Int16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.SByte>|<span data-ttu-id="d7223-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-111"><xref:System.Int16>, <xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="d7223-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-112"><xref:System.Int32>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="d7223-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-113"><xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Char>|<span data-ttu-id="d7223-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-114"><xref:System.UInt16>, <xref:System.UInt32>, <xref:System.Int32>, <xref:System.UInt64>, <xref:System.Int64>, <xref:System.Single>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="d7223-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-115"><xref:System.Int64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="d7223-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span><span class="sxs-lookup"><span data-stu-id="d7223-116"><xref:System.Int64>, <xref:System.UInt64>, <xref:System.Double>, <xref:System.Decimal></span></span>|  
|<xref:System.Int64>|<xref:System.Decimal>|  
|<xref:System.UInt64>|<xref:System.Decimal>|  
|<xref:System.Single>|<xref:System.Double>|  
  
 <span data-ttu-id="d7223-117">Niektóre rozszerzanie konwersji do <xref:System.Single> lub <xref:System.Double> może spowodować utratę dokładności.</span><span class="sxs-lookup"><span data-stu-id="d7223-117">Some widening conversions to <xref:System.Single> or <xref:System.Double> can cause a loss of precision.</span></span> <span data-ttu-id="d7223-118">W poniższej tabeli opisano konwersje rozszerzającą, które czasami spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="d7223-118">The following table describes the widening conversions that sometimes result in a loss of information.</span></span>  
  
|<span data-ttu-id="d7223-119">Typ</span><span class="sxs-lookup"><span data-stu-id="d7223-119">Type</span></span>|<span data-ttu-id="d7223-120">Może zostać przekonwertowany na</span><span class="sxs-lookup"><span data-stu-id="d7223-120">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Int32>|<xref:System.Single>|  
|<xref:System.UInt32>|<xref:System.Single>|  
|<xref:System.Int64>|<span data-ttu-id="d7223-121"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="d7223-121"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="d7223-122"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="d7223-122"><xref:System.Single>, <xref:System.Double></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="d7223-123"><xref:System.Single>, <xref:System.Double></span><span class="sxs-lookup"><span data-stu-id="d7223-123"><xref:System.Single>, <xref:System.Double></span></span>|  
  
## <a name="narrowing-conversions"></a><span data-ttu-id="d7223-124">Zawężanie konwersji</span><span class="sxs-lookup"><span data-stu-id="d7223-124">Narrowing Conversions</span></span>  
 <span data-ttu-id="d7223-125">Do konwersji zawężającej <xref:System.Single> lub <xref:System.Double> może spowodować utratę danych.</span><span class="sxs-lookup"><span data-stu-id="d7223-125">A narrowing conversion to <xref:System.Single> or <xref:System.Double> can cause a loss of information.</span></span> <span data-ttu-id="d7223-126">Jeśli typ docelowy nie może poprawnie express wielkości źródła, wynikowy typ jest ustawiony na stałą `PositiveInfinity` lub `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="d7223-126">If the target type cannot properly express the magnitude of the source, the resulting type is set to the constant `PositiveInfinity` or `NegativeInfinity`.</span></span> <span data-ttu-id="d7223-127">`PositiveInfinity`wyniki z dzielenia przez zero dodatnia i jest także zwracany kiedy wartość <xref:System.Single> lub <xref:System.Double> przekracza wartość `MaxValue` pola.</span><span class="sxs-lookup"><span data-stu-id="d7223-127">`PositiveInfinity` results from dividing a positive number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> exceeds the value of the `MaxValue` field.</span></span> <span data-ttu-id="d7223-128">`NegativeInfinity`wyniki z dzielenia przez zero ujemna i jest także zwracany kiedy wartość <xref:System.Single> lub <xref:System.Double> spadnie poniżej wartości `MinValue` pola.</span><span class="sxs-lookup"><span data-stu-id="d7223-128">`NegativeInfinity` results from dividing a negative number by zero and is also returned when the value of a <xref:System.Single> or <xref:System.Double> falls below the value of the `MinValue` field.</span></span> <span data-ttu-id="d7223-129">Konwersja z <xref:System.Double> do <xref:System.Single> może spowodować `PositiveInfinity` lub `NegativeInfinity`.</span><span class="sxs-lookup"><span data-stu-id="d7223-129">A conversion from a <xref:System.Double> to a <xref:System.Single> might result in `PositiveInfinity` or `NegativeInfinity`.</span></span>  
  
 <span data-ttu-id="d7223-130">Konwersji zawężającej również może spowodować utratę danych dla innych typów danych.</span><span class="sxs-lookup"><span data-stu-id="d7223-130">A narrowing conversion can also result in a loss of information for other data types.</span></span> <span data-ttu-id="d7223-131">Jednak <xref:System.OverflowException> jest generowany, jeśli wartość typu, który jest przekształcany jest spoza zakresu określonego przez typ docelowy `MaxValue` i `MinValue` pola i konwersji jest sprawdzana przez środowiska uruchomieniowego upewnij się, że wartość elementu docelowego Typ nie może przekraczać jego `MaxValue` lub `MinValue`.</span><span class="sxs-lookup"><span data-stu-id="d7223-131">However, an <xref:System.OverflowException> is thrown if the value of a type that is being converted falls outside of the range specified by the target type's `MaxValue` and `MinValue` fields, and the conversion is checked by the runtime to ensure that the value of the target type does not exceed its `MaxValue` or `MinValue`.</span></span> <span data-ttu-id="d7223-132">Konwersje, które są wykonywane z <xref:System.Convert?displayProperty=nameWithType> klasy zawsze są sprawdzane w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="d7223-132">Conversions that are performed with the <xref:System.Convert?displayProperty=nameWithType> class are always checked in this manner.</span></span>  
  
 <span data-ttu-id="d7223-133">W poniższej tabeli wymieniono konwersje, które zgłaszają <xref:System.OverflowException> przy użyciu <xref:System.Convert?displayProperty=nameWithType> lub dowolny wybrany konwersji, jeśli jest wartość typu konwertowanej do zdefiniowanego zakresu wynikowy typ.</span><span class="sxs-lookup"><span data-stu-id="d7223-133">The following table lists conversions that throw an <xref:System.OverflowException> using <xref:System.Convert?displayProperty=nameWithType> or any checked conversion if the value of the type being converted is outside the defined range of the resulting type.</span></span>  
  
|<span data-ttu-id="d7223-134">Typ</span><span class="sxs-lookup"><span data-stu-id="d7223-134">Type</span></span>|<span data-ttu-id="d7223-135">Może zostać przekonwertowany na</span><span class="sxs-lookup"><span data-stu-id="d7223-135">Can be converted to</span></span>|  
|----------|-------------------------|  
|<xref:System.Byte>|<xref:System.SByte>|  
|<xref:System.SByte>|<span data-ttu-id="d7223-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="d7223-136"><xref:System.Byte>, <xref:System.UInt16>, <xref:System.UInt32>, <xref:System.UInt64></span></span>|  
|<xref:System.Int16>|<span data-ttu-id="d7223-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span><span class="sxs-lookup"><span data-stu-id="d7223-137"><xref:System.Byte>, <xref:System.SByte>, <xref:System.UInt16></span></span>|  
|<xref:System.UInt16>|<span data-ttu-id="d7223-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span><span class="sxs-lookup"><span data-stu-id="d7223-138"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16></span></span>|  
|<xref:System.Int32>|<span data-ttu-id="d7223-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span><span class="sxs-lookup"><span data-stu-id="d7223-139"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>,<xref:System.UInt32></span></span>|  
|<xref:System.UInt32>|<span data-ttu-id="d7223-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span><span class="sxs-lookup"><span data-stu-id="d7223-140"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32></span></span>|  
|<xref:System.Int64>|<span data-ttu-id="d7223-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="d7223-141"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>,<xref:System.UInt32>,<xref:System.UInt64></span></span>|  
|<xref:System.UInt64>|<span data-ttu-id="d7223-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span><span class="sxs-lookup"><span data-stu-id="d7223-142"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64></span></span>|  
|<xref:System.Decimal>|<span data-ttu-id="d7223-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="d7223-143"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Single>|<span data-ttu-id="d7223-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="d7223-144"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
|<xref:System.Double>|<span data-ttu-id="d7223-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span><span class="sxs-lookup"><span data-stu-id="d7223-145"><xref:System.Byte>, <xref:System.SByte>, <xref:System.Int16>, <xref:System.UInt16>, <xref:System.Int32>, <xref:System.UInt32>, <xref:System.Int64>, <xref:System.UInt64></span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d7223-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d7223-146">See Also</span></span>  
 <xref:System.Convert?displayProperty=nameWithType>  
 [<span data-ttu-id="d7223-147">Konwersja typów w programie .NET</span><span class="sxs-lookup"><span data-stu-id="d7223-147">Type Conversion in .NET</span></span>](../../../docs/standard/base-types/type-conversion.md)
