---
title: Typy kopiowalne i niekopiowalne
description: Dowiedz się więcej o typach danych kopiowalnych i innych niż danych kopiowalnych. Typy danych danych kopiowalnych są często reprezentowane w pamięci zarządzanej i niezarządzanej i nie wymagają specjalnej obsługi.
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
ms.openlocfilehash: 68f4197a2710b6825c83bbc51daaf8f6b5a2c81f
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621538"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="eafc6-104">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="eafc6-104">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="eafc6-105">Większość typów danych ma wspólną reprezentację w pamięci zarządzanej i niezarządzanej i nie wymaga specjalnej obsługi przez organizatora międzyoperacyjności.</span><span class="sxs-lookup"><span data-stu-id="eafc6-105">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="eafc6-106">Typy te są nazywane *danych kopiowalnychmi* , ponieważ nie wymagają konwersji podczas przekazywania między zarządzanym i niezarządzanym kodem.</span><span class="sxs-lookup"><span data-stu-id="eafc6-106">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="eafc6-107">Struktury zwracane z wywołań wywołania platformy muszą być typami danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-107">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="eafc6-108">Wywołanie platformy nie obsługuje struktur innych niż danych kopiowalnych jako typów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-108">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="eafc6-109">Następujące typy z <xref:System> przestrzeni nazw są typami danych kopiowalnych:</span><span class="sxs-lookup"><span data-stu-id="eafc6-109">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
- <xref:System.Byte?displayProperty=nameWithType>  
  
- <xref:System.SByte?displayProperty=nameWithType>  
  
- <xref:System.Int16?displayProperty=nameWithType>  
  
- <xref:System.UInt16?displayProperty=nameWithType>  
  
- <xref:System.Int32?displayProperty=nameWithType>  
  
- <xref:System.UInt32?displayProperty=nameWithType>  
  
- <xref:System.Int64?displayProperty=nameWithType>  
  
- <xref:System.UInt64?displayProperty=nameWithType>  
  
- <xref:System.IntPtr?displayProperty=nameWithType>  
  
- <xref:System.UIntPtr?displayProperty=nameWithType>  
  
- <xref:System.Single?displayProperty=nameWithType>  
  
- <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="eafc6-110">Następujące typy złożone są również danych kopiowalnych:</span><span class="sxs-lookup"><span data-stu-id="eafc6-110">The following complex types are also blittable types:</span></span>  
  
- <span data-ttu-id="eafc6-111">Jednowymiarowe tablice typów danych kopiowalnych, takie jak tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-111">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="eafc6-112">Jednak typ, który zawiera zmienną tablicę typów danych kopiowalnych, nie należy do siebie danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-112">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
- <span data-ttu-id="eafc6-113">Sformatowane typy wartości, które zawierają tylko typy danych kopiowalnych (i klasy, jeśli są organizowane jako sformatowane typy).</span><span class="sxs-lookup"><span data-stu-id="eafc6-113">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="eafc6-114">Aby uzyskać więcej informacji na temat sformatowanych typów wartości, zobacz [domyślne kierowanie dla typów wartości](default-marshaling-behavior.md#default-marshaling-for-value-types).</span><span class="sxs-lookup"><span data-stu-id="eafc6-114">For more information about formatted value types, see [Default marshaling for value types](default-marshaling-behavior.md#default-marshaling-for-value-types).</span></span>  
  
 <span data-ttu-id="eafc6-115">Odwołania do obiektów nie są danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-115">Object references are not blittable.</span></span> <span data-ttu-id="eafc6-116">Obejmuje to tablicę odwołań do obiektów, które są danych kopiowalnych przez siebie.</span><span class="sxs-lookup"><span data-stu-id="eafc6-116">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="eafc6-117">Na przykład można zdefiniować strukturę danych kopiowalnych, ale nie można zdefiniować typu danych kopiowalnych, który zawiera tablicę odwołań do tych struktur.</span><span class="sxs-lookup"><span data-stu-id="eafc6-117">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="eafc6-118">Jako Optymalizacja, tablice typów danych kopiowalnych i klas, które zawierają tylko składowe danych kopiowalnych, są [przypięte](copying-and-pinning.md) zamiast kopiowane podczas organizowania.</span><span class="sxs-lookup"><span data-stu-id="eafc6-118">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="eafc6-119">Te typy mogą być organizowane jako parametry wejściowe/out, gdy wywołujący i wywoływany są w tym samym elemencie Apartment.</span><span class="sxs-lookup"><span data-stu-id="eafc6-119">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="eafc6-120">Jednak te typy są faktycznie organizowane jako parametry i należy zastosować <xref:System.Runtime.InteropServices.InAttribute> atrybuty i, <xref:System.Runtime.InteropServices.OutAttribute> Jeśli chcesz zorganizować argument jako parametr in/out.</span><span class="sxs-lookup"><span data-stu-id="eafc6-120">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="eafc6-121">Niektóre typy danych zarządzanych wymagają innej reprezentacji w niezarządzanym środowisku.</span><span class="sxs-lookup"><span data-stu-id="eafc6-121">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="eafc6-122">Te typy danych inne niż danych kopiowalnych muszą zostać przekonwertowane na formularz, który może być zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="eafc6-122">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="eafc6-123">Na przykład, zarządzanymi ciągami są typy inne niż danych kopiowalnych, ponieważ muszą one być konwertowane do obiektów String, zanim będą mogły być organizowane.</span><span class="sxs-lookup"><span data-stu-id="eafc6-123">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="eafc6-124">Poniższa tabela zawiera listę typów innych niż danych kopiowalnych z <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="eafc6-124">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="eafc6-125">[Delegaty](default-marshaling-behavior.md#default-marshaling-for-delegates), które są strukturami danych, które odwołują się do metody statycznej lub do wystąpienia klasy, również nie są danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="eafc6-125">[Delegates](default-marshaling-behavior.md#default-marshaling-for-delegates), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="eafc6-126">Typ inny niż danych kopiowalnych</span><span class="sxs-lookup"><span data-stu-id="eafc6-126">Non-blittable type</span></span>|<span data-ttu-id="eafc6-127">Opis</span><span class="sxs-lookup"><span data-stu-id="eafc6-127">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="eafc6-128">System. Array</span><span class="sxs-lookup"><span data-stu-id="eafc6-128">System.Array</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="eafc6-129">Konwertuje na tablicę w stylu C lub `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="eafc6-129">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="eafc6-130">[System. Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eafc6-130">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="eafc6-131">Konwertuje do wartości 1, 2 lub 4-bajtowej na wartość `true` 1 lub-1.</span><span class="sxs-lookup"><span data-stu-id="eafc6-131">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="eafc6-132">[System. Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eafc6-132">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="eafc6-133">Konwertuje na znak Unicode lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="eafc6-133">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="eafc6-134">[System. Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eafc6-134">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="eafc6-135">Konwertuje do interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="eafc6-135">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="eafc6-136">System.Object</span><span class="sxs-lookup"><span data-stu-id="eafc6-136">System.Object</span></span>](default-marshaling-for-objects.md)|<span data-ttu-id="eafc6-137">Konwertuje na wariant lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="eafc6-137">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="eafc6-138">System. Mdarray</span><span class="sxs-lookup"><span data-stu-id="eafc6-138">System.Mdarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="eafc6-139">Konwertuje na tablicę w stylu C lub `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="eafc6-139">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="eafc6-140">System. String</span><span class="sxs-lookup"><span data-stu-id="eafc6-140">System.String</span></span>](default-marshaling-for-strings.md)|<span data-ttu-id="eafc6-141">Konwertuje na ciąg kończący się w odwołaniu o wartości null lub w postaci BSTR.</span><span class="sxs-lookup"><span data-stu-id="eafc6-141">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="eafc6-142">[System. ValueType](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="eafc6-142">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="eafc6-143">Konwertuje na strukturę ze stałym układem pamięci.</span><span class="sxs-lookup"><span data-stu-id="eafc6-143">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="eafc6-144">System. Szarray</span><span class="sxs-lookup"><span data-stu-id="eafc6-144">System.Szarray</span></span>](default-marshaling-for-arrays.md)|<span data-ttu-id="eafc6-145">Konwertuje na tablicę w stylu C lub `SAFEARRAY` .</span><span class="sxs-lookup"><span data-stu-id="eafc6-145">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="eafc6-146">Typy klas i obiektów są obsługiwane tylko przez międzyoperacyjność modelu COM.</span><span class="sxs-lookup"><span data-stu-id="eafc6-146">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="eafc6-147">Aby uzyskać odpowiednie typy w Visual Basic, C# i C++, zobacz [Omówienie biblioteki klas](../../standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="eafc6-147">For corresponding types in Visual Basic, C#, and C++, see the [Class Library Overview](../../standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eafc6-148">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="eafc6-148">See also</span></span>

- [<span data-ttu-id="eafc6-149">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="eafc6-149">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
