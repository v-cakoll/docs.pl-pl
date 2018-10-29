---
title: Typy kopiowalne i niekopiowalne
ms.date: 03/30/2017
helpviewer_keywords:
- interop marshaling, blittable types
- blittable types, interop marshaling
ms.assetid: d03b050e-2916-49a0-99ba-f19316e5c1b3
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8b4c1d213c2ed87126fc5eb9995050e14f9214bd
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2018
ms.locfileid: "50199841"
---
# <a name="blittable-and-non-blittable-types"></a><span data-ttu-id="9619e-102">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="9619e-102">Blittable and Non-Blittable Types</span></span>
<span data-ttu-id="9619e-103">Większość typów danych mają wspólne reprezentacji w pamięci zarządzanych i niezarządzanych i nie wymagają specjalnej obsługi, organizator międzyoperacyjny.</span><span class="sxs-lookup"><span data-stu-id="9619e-103">Most data types have a common representation in both managed and unmanaged memory and do not require special handling by the interop marshaler.</span></span> <span data-ttu-id="9619e-104">Te typy są nazywane *kopiowalnymi* , ponieważ nie wymaga konwersji, gdy są one przekazywane między kodu zarządzanego i niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="9619e-104">These types are called *blittable types* because they do not require conversion when they are passed between managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="9619e-105">Wywołania struktury, które są zwracane z platformy musi być typy danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="9619e-105">Structures that are returned from platform invoke calls must be blittable types.</span></span> <span data-ttu-id="9619e-106">Wywołanie platformy nie obsługuje struktury niekopiowalnych jako typów zwracanych.</span><span class="sxs-lookup"><span data-stu-id="9619e-106">Platform invoke does not support non-blittable structures as return types.</span></span>  
  
 <span data-ttu-id="9619e-107">Następujące typy z <xref:System> nazw są typy danych kopiowalnych:</span><span class="sxs-lookup"><span data-stu-id="9619e-107">The following types from the <xref:System> namespace are blittable types:</span></span>  
  
-   <xref:System.Byte?displayProperty=nameWithType>  
  
-   <xref:System.SByte?displayProperty=nameWithType>  
  
-   <xref:System.Int16?displayProperty=nameWithType>  
  
-   <xref:System.UInt16?displayProperty=nameWithType>  
  
-   <xref:System.Int32?displayProperty=nameWithType>  
  
-   <xref:System.UInt32?displayProperty=nameWithType>  
  
-   <xref:System.Int64?displayProperty=nameWithType>  
  
-   <xref:System.UInt64?displayProperty=nameWithType>  
  
-   <xref:System.IntPtr?displayProperty=nameWithType>  
  
-   <xref:System.UIntPtr?displayProperty=nameWithType>  
  
-   <xref:System.Single?displayProperty=nameWithType>  
  
-   <xref:System.Double?displayProperty=nameWithType>  
  
 <span data-ttu-id="9619e-108">Typy danych kopiowalnych są również następujące typy złożone:</span><span class="sxs-lookup"><span data-stu-id="9619e-108">The following complex types are also blittable types:</span></span>  
  
-   <span data-ttu-id="9619e-109">Tablice jednowymiarowe typów danych kopiowalnych, takich jak tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="9619e-109">One-dimensional arrays of blittable types, such as an array of integers.</span></span> <span data-ttu-id="9619e-110">Typ, który zawiera zmienną tablicy typów danych kopiowalnych nie jest jednak sam danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="9619e-110">However, a type that contains a variable array of blittable types is not itself blittable.</span></span>  
  
-   <span data-ttu-id="9619e-111">Typy sformatowanej wartości, które zawierają typy danych kopiowalnych tylko (i klasy, jeśli są one organizowane jak sformatowane typy).</span><span class="sxs-lookup"><span data-stu-id="9619e-111">Formatted value types that contain only blittable types (and classes if they are marshaled as formatted types).</span></span> <span data-ttu-id="9619e-112">Aby uzyskać więcej informacji na temat typów sformatowaną wartość zobacz [domyślny Marshaling dla typów wartości](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="9619e-112">For more information about formatted value types, see [Default Marshaling for Value Types](https://msdn.microsoft.com/library/4d9a876c-e05a-40ba-bd85-bd22877f984a(v=vs.100)).</span></span>  
  
 <span data-ttu-id="9619e-113">Odwołania do obiektu nie są danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="9619e-113">Object references are not blittable.</span></span> <span data-ttu-id="9619e-114">Obejmuje to tablica odniesień do obiektów, które danych kopiowalnych samodzielnie.</span><span class="sxs-lookup"><span data-stu-id="9619e-114">This includes an array of references to objects that are blittable by themselves.</span></span> <span data-ttu-id="9619e-115">Na przykład można zdefiniować strukturę danych kopiowalnych, ale nie można zdefiniować typ danych kopiowalnych, który zawiera szereg odwołań do tych struktur.</span><span class="sxs-lookup"><span data-stu-id="9619e-115">For example, you can define a structure that is blittable, but you cannot define a blittable type that contains an array of references to those structures.</span></span>  
  
 <span data-ttu-id="9619e-116">Optymalizacji, są tablicami typy kopiowalne i klas, które zawierają tylko elementy członkowskie danych kopiowalnych [przypięte](../../../docs/framework/interop/copying-and-pinning.md) zamiast kopiowane podczas przekazywania międzyprocesowego.</span><span class="sxs-lookup"><span data-stu-id="9619e-116">As an optimization, arrays of blittable types and classes that contain only blittable members are [pinned](../../../docs/framework/interop/copying-and-pinning.md) instead of copied during marshaling.</span></span> <span data-ttu-id="9619e-117">Te typy może okazać się być organizowany jako we/wy parametrów, gdy obiektami wywołującym i wywoływanym znajdują się w tej samej typu apartment.</span><span class="sxs-lookup"><span data-stu-id="9619e-117">These types can appear to be marshaled as In/Out parameters when the caller and callee are in the same apartment.</span></span> <span data-ttu-id="9619e-118">Jednak te typy są faktycznie przekazywane tak jak parametry i należy najpierw zastosować <xref:System.Runtime.InteropServices.InAttribute> i <xref:System.Runtime.InteropServices.OutAttribute> atrybuty, jeśli chcesz zorganizować argument jako In/Out parametru.</span><span class="sxs-lookup"><span data-stu-id="9619e-118">However, these types are actually marshaled as In parameters, and you must apply the <xref:System.Runtime.InteropServices.InAttribute> and <xref:System.Runtime.InteropServices.OutAttribute> attributes if you want to marshal the argument as an In/Out parameter.</span></span>  
  
 <span data-ttu-id="9619e-119">Niektóre typy zarządzanych danych wymagają różnych reprezentacji w środowisku niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="9619e-119">Some managed data types require a different representation in an unmanaged environment.</span></span> <span data-ttu-id="9619e-120">Te typy danych niekopiowalnych należy przekonwertować do formularza, który może być organizowany.</span><span class="sxs-lookup"><span data-stu-id="9619e-120">These non-blittable data types must be converted into a form that can be marshaled.</span></span> <span data-ttu-id="9619e-121">Na przykład ciągi zarządzane są typów niekopiowalnych, ponieważ muszą zostać przekonwertowane na obiektów w postaci ciągów, zanim one może być organizowany.</span><span class="sxs-lookup"><span data-stu-id="9619e-121">For example, managed strings are non-blittable types because they must be converted into string objects before they can be marshaled.</span></span>  
  
 <span data-ttu-id="9619e-122">Poniższa tabela zawiera listę typów niekopiowalnych z <xref:System> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="9619e-122">The following table lists non-blittable types from the <xref:System> namespace.</span></span> <span data-ttu-id="9619e-123">[Delegaty](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), służą do struktur danych, które odwołują się do statycznej metody lub wystąpienia klasy, są również niekopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="9619e-123">[Delegates](https://msdn.microsoft.com/library/d176ee76-f982-494b-b03d-92e4118896e2(v=vs.100)), which are data structures that refer to a static method or to a class instance, are also non-blittable.</span></span>  
  
|<span data-ttu-id="9619e-124">Typ danych kopiowalnych inne niż</span><span class="sxs-lookup"><span data-stu-id="9619e-124">Non-blittable type</span></span>|<span data-ttu-id="9619e-125">Opis</span><span class="sxs-lookup"><span data-stu-id="9619e-125">Description</span></span>|  
|-------------------------|-----------------|  
|[<span data-ttu-id="9619e-126">System.Array</span><span class="sxs-lookup"><span data-stu-id="9619e-126">System.Array</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="9619e-127">Konwertuje tablicy stylu C lub `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="9619e-127">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|<span data-ttu-id="9619e-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9619e-128">[System.Boolean](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/t2t3725f(v=vs.100))</span></span>|<span data-ttu-id="9619e-129">Konwertuje wartość 1, 2 lub 4-bajtową wartością `true` jako 1 lub -1.</span><span class="sxs-lookup"><span data-stu-id="9619e-129">Converts to a 1, 2, or 4-byte value with `true` as 1 or -1.</span></span>|  
|<span data-ttu-id="9619e-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9619e-130">[System.Char](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/6tyybbf2(v=vs.100))</span></span>|<span data-ttu-id="9619e-131">Konwertuje znak Unicode lub ANSI.</span><span class="sxs-lookup"><span data-stu-id="9619e-131">Converts to a Unicode or ANSI character.</span></span>|  
|<span data-ttu-id="9619e-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9619e-132">[System.Class](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/s0968xy8(v=vs.100))</span></span>|<span data-ttu-id="9619e-133">Konwertuje interfejsu klasy.</span><span class="sxs-lookup"><span data-stu-id="9619e-133">Converts to a class interface.</span></span>|  
|[<span data-ttu-id="9619e-134">System.Object</span><span class="sxs-lookup"><span data-stu-id="9619e-134">System.Object</span></span>](../../../docs/framework/interop/default-marshaling-for-objects.md)|<span data-ttu-id="9619e-135">Konwertuje typ variant lub interfejs.</span><span class="sxs-lookup"><span data-stu-id="9619e-135">Converts to a variant or an interface.</span></span>|  
|[<span data-ttu-id="9619e-136">System.Mdarray</span><span class="sxs-lookup"><span data-stu-id="9619e-136">System.Mdarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="9619e-137">Konwertuje tablicy stylu C lub `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="9619e-137">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
|[<span data-ttu-id="9619e-138">System.String</span><span class="sxs-lookup"><span data-stu-id="9619e-138">System.String</span></span>](../../../docs/framework/interop/default-marshaling-for-strings.md)|<span data-ttu-id="9619e-139">Konwertuje ciąg przerywa w odwołanie o wartości null lub ciąg BSTR.</span><span class="sxs-lookup"><span data-stu-id="9619e-139">Converts to a string terminating in a null reference or to a BSTR.</span></span>|  
|<span data-ttu-id="9619e-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="9619e-140">[System.Valuetype](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/0t2cwe11(v=vs.100))</span></span>|<span data-ttu-id="9619e-141">Konwertuje struktury z układem stały pamięci.</span><span class="sxs-lookup"><span data-stu-id="9619e-141">Converts to a structure with a fixed memory layout.</span></span>|  
|[<span data-ttu-id="9619e-142">System.Szarray</span><span class="sxs-lookup"><span data-stu-id="9619e-142">System.Szarray</span></span>](../../../docs/framework/interop/default-marshaling-for-arrays.md)|<span data-ttu-id="9619e-143">Konwertuje tablicy stylu C lub `SAFEARRAY`.</span><span class="sxs-lookup"><span data-stu-id="9619e-143">Converts to a C-style array or a `SAFEARRAY`.</span></span>|  
  
 <span data-ttu-id="9619e-144">Typy klas i obiektów są obsługiwane tylko przez współdziałania z modelem COM.</span><span class="sxs-lookup"><span data-stu-id="9619e-144">Class and object types are supported only by COM interop.</span></span> <span data-ttu-id="9619e-145">Dla odpowiednich typów w pakietach [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#i C++, zobacz [Przegląd biblioteki klas](../../../docs/standard/class-library-overview.md).</span><span class="sxs-lookup"><span data-stu-id="9619e-145">For corresponding types in [!INCLUDE[vbprvblong](../../../includes/vbprvblong-md.md)], C#, and C++, see the [Class Library Overview](../../../docs/standard/class-library-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9619e-146">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9619e-146">See Also</span></span>  
 [<span data-ttu-id="9619e-147">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="9619e-147">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)
