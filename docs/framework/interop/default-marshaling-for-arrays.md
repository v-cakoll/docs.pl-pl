---
title: Organizowanie domyślne dotyczące tablic
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
ms.openlocfilehash: f0094ac572834b2cf0d74fb53c94877da55669e2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181452"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="d201c-102">Organizowanie domyślne dotyczące tablic</span><span class="sxs-lookup"><span data-stu-id="d201c-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="d201c-103">W aplikacji składającej się w całości z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako parametry W/Out.</span><span class="sxs-lookup"><span data-stu-id="d201c-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="d201c-104">Z drugiej strony organizator międzypłeczny przekazuje tablicy jako w parametrach domyślnie.</span><span class="sxs-lookup"><span data-stu-id="d201c-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="d201c-105">Dzięki [optymalizacji przypinania](copying-and-pinning.md)tablica blittable może działać jako parametr In/Out podczas interakcji z obiektami w tym samym mieszkaniu.</span><span class="sxs-lookup"><span data-stu-id="d201c-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="d201c-106">Jednak jeśli później wyeksportować kod do biblioteki typów używane do generowania serwera proxy między komputerami i tej biblioteki jest używany do organizowania wywołań w apartamentach, wywołania można przywrócić true w zachowanie parametru.</span><span class="sxs-lookup"><span data-stu-id="d201c-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="d201c-107">Tablice są złożone z natury, a różnice między tablicami zarządzanymi i niezarządzanymi wymagają więcej informacji niż inne typy, których nie można uzyskać.</span><span class="sxs-lookup"><span data-stu-id="d201c-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="d201c-108">Tablice zarządzane</span><span class="sxs-lookup"><span data-stu-id="d201c-108">Managed Arrays</span></span>  
 <span data-ttu-id="d201c-109">Typy tablic zarządzanych mogą się różnić; jednak <xref:System.Array?displayProperty=nameWithType> klasa jest klasą podstawową wszystkich typów tablic.</span><span class="sxs-lookup"><span data-stu-id="d201c-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="d201c-110">**Klasa System.Array** ma właściwości określania rangi, długości oraz dolnej i górnej granicy tablicy, a także metody uzyskiwania dostępu, sortowania, wyszukiwania, kopiowania i tworzenia tablic.</span><span class="sxs-lookup"><span data-stu-id="d201c-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="d201c-111">Te typy tablic są dynamiczne i nie mają odpowiedniego typu statycznego zdefiniowanego w bibliotece klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="d201c-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="d201c-112">Jest to wygodne, aby myśleć o każdej kombinacji typu elementu i rangi jako odrębny typ tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="d201c-113">W związku z tym jednowymiarowa tablica liczby całkowitej jest innego typu niż jednowymiarowa tablica typów podwójnych.</span><span class="sxs-lookup"><span data-stu-id="d201c-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="d201c-114">Podobnie dwuwymiarowa tablica liczby całkowitych różni się od jednowymiarowej tablicy liczby całkowitej.</span><span class="sxs-lookup"><span data-stu-id="d201c-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="d201c-115">Granice tablicy nie są brane pod uwagę podczas porównywania typów.</span><span class="sxs-lookup"><span data-stu-id="d201c-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="d201c-116">Jak pokazano w poniższej tabeli, każde wystąpienie tablicy zarządzanej musi mieć określony typ elementu, rangę i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="d201c-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="d201c-117">Typ tablicy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="d201c-117">Managed array type</span></span>|<span data-ttu-id="d201c-118">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="d201c-118">Element type</span></span>|<span data-ttu-id="d201c-119">Ranga</span><span class="sxs-lookup"><span data-stu-id="d201c-119">Rank</span></span>|<span data-ttu-id="d201c-120">Dolna granica</span><span class="sxs-lookup"><span data-stu-id="d201c-120">Lower bound</span></span>|<span data-ttu-id="d201c-121">Notacja podpisu</span><span class="sxs-lookup"><span data-stu-id="d201c-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="d201c-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="d201c-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="d201c-123">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="d201c-123">Specified by type.</span></span>|<span data-ttu-id="d201c-124">Określona według rangi.</span><span class="sxs-lookup"><span data-stu-id="d201c-124">Specified by rank.</span></span>|<span data-ttu-id="d201c-125">Opcjonalnie określone przez granice.</span><span class="sxs-lookup"><span data-stu-id="d201c-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="d201c-126">*typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="d201c-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="d201c-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="d201c-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="d201c-128">Nieznane</span><span class="sxs-lookup"><span data-stu-id="d201c-128">Unknown</span></span>|<span data-ttu-id="d201c-129">Nieznane</span><span class="sxs-lookup"><span data-stu-id="d201c-129">Unknown</span></span>|<span data-ttu-id="d201c-130">Nieznane</span><span class="sxs-lookup"><span data-stu-id="d201c-130">Unknown</span></span>|<span data-ttu-id="d201c-131">**System.array**</span><span class="sxs-lookup"><span data-stu-id="d201c-131">**System.Array**</span></span>|  
|<span data-ttu-id="d201c-132">**Element_type_szarray**</span><span class="sxs-lookup"><span data-stu-id="d201c-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="d201c-133">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="d201c-133">Specified by type.</span></span>|<span data-ttu-id="d201c-134">1</span><span class="sxs-lookup"><span data-stu-id="d201c-134">1</span></span>|<span data-ttu-id="d201c-135">0</span><span class="sxs-lookup"><span data-stu-id="d201c-135">0</span></span>|<span data-ttu-id="d201c-136">*typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="d201c-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="d201c-137">Tablice niezarządzane</span><span class="sxs-lookup"><span data-stu-id="d201c-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="d201c-138">Tablice niezarządzane są tablicami bezpiecznymi w stylu COM lub tablicami w stylu C o stałej lub zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="d201c-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="d201c-139">Bezpieczne tablice są samookryczające tablice, które zawierają typ, rangę i granice skojarzonych danych tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="d201c-140">Tablice w stylu C są jednowymiarowymi tablicami wpisanych o stałej dolnej granicy 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="d201c-141">Usługa organizowania ma ograniczoną obsługę dla obu typów tablic.</span><span class="sxs-lookup"><span data-stu-id="d201c-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="d201c-142">Przekazywanie parametrów tablicy do kodu NET</span><span class="sxs-lookup"><span data-stu-id="d201c-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="d201c-143">Zarówno tablice w stylu C, jak i bezpieczne tablice mogą być przekazywane do kodu .NET z kodu niezarządzanego jako tablica bezpieczna lub tablica w stylu C.</span><span class="sxs-lookup"><span data-stu-id="d201c-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="d201c-144">W poniższej tabeli przedstawiono wartość typu niezarządzanego i typ zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="d201c-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="d201c-145">Typ niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-145">Unmanaged type</span></span>|<span data-ttu-id="d201c-146">Typ zaimportowany</span><span class="sxs-lookup"><span data-stu-id="d201c-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="d201c-147">**SafeArray(** *Typ* **)**</span><span class="sxs-lookup"><span data-stu-id="d201c-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="d201c-148">**\<** **ELEMENT_TYPE_SZARRAY** *ConvertedType\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="d201c-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="d201c-149">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="d201c-150">Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d201c-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="d201c-151">Bezpieczne tablice, które nie są rangą = 1 lub dolna granica = 0 nie mogą być organizowane jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="d201c-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="d201c-152">*Typ*  **[]**</span><span class="sxs-lookup"><span data-stu-id="d201c-152">*Type*  **[]**</span></span>|<span data-ttu-id="d201c-153">**\<** **ELEMENT_TYPE_SZARRAY** *ConvertedType\*\*\*>*\*</span><span class="sxs-lookup"><span data-stu-id="d201c-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="d201c-154">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="d201c-155">Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d201c-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="d201c-156">Bezpieczne tablice</span><span class="sxs-lookup"><span data-stu-id="d201c-156">Safe Arrays</span></span>  
 <span data-ttu-id="d201c-157">Gdy bezpieczna tablica jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na tablicę jednowymiarową znanego typu (na przykład **int).**</span><span class="sxs-lookup"><span data-stu-id="d201c-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="d201c-158">Te same reguły konwersji typu, które mają zastosowanie do parametrów, mają również zastosowanie do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="d201c-159">Na przykład bezpieczna tablica typów **BSTR** staje się zarządzaną tablicą ciągów, a bezpieczna tablica wariantów staje się zarządzaną tablicą obiektów.</span><span class="sxs-lookup"><span data-stu-id="d201c-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="d201c-160">Typ elementu **SAFEARRAY** jest przechwytywany z biblioteki typów i <xref:System.Runtime.InteropServices.UnmanagedType> zapisywany w wartości **SAFEARRAY** wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="d201c-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="d201c-161">Ponieważ rangi i granice tablicy bezpieczne nie można określić z biblioteki typów, ranga zakłada się, że równa 1 i dolnej granicy zakłada się równe 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="d201c-162">Ranga i granice muszą być zdefiniowane w podpisie zarządzanym sporządzonym przez [importera biblioteki typów (Tlbimp.exe).](../tools/tlbimp-exe-type-library-importer.md)</span><span class="sxs-lookup"><span data-stu-id="d201c-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="d201c-163">Jeśli ranga przeszedł do metody w czasie <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> wykonywania różni się, a jest wyrzucany.</span><span class="sxs-lookup"><span data-stu-id="d201c-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="d201c-164">Jeśli typ tablicy przekazywane w czasie wykonywania <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> różni się, a jest generowany.</span><span class="sxs-lookup"><span data-stu-id="d201c-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="d201c-165">Poniższy przykład przedstawia bezpieczne tablice w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="d201c-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="d201c-166">**Podpis niezarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-166">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="d201c-167">**Podpis zarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-167">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_I4)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_DATE)> _
   ar() As DateTime)  
Sub New3(ByRef <MarshalAs(UnmanagedType.SafeArray, SafeArraySubType:=VT_BSTR)> _
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_I4)] int[] ar) ;  
void New2([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_DATE)]
   DateTime[] ar);  
void New3([MarshalAs(UnmanagedType.SafeArray, SafeArraySubType=VT_BSTR)]
   ref String[] ar);  
```  
  
 <span data-ttu-id="d201c-168">Tablice wielowymiarowe lub niezerowe mogą być kierowane do kodu zarządzanego, jeśli podpis metody wyprodukowany przez Tlbimp.exe zostanie zmodyfikowany w celu wskazania typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="d201c-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="d201c-169">Alternatywnie można użyć **przełącznika /sysarray** z Tlbimp.exe, <xref:System.Array?displayProperty=nameWithType> aby zaimportować wszystkie tablice jako obiekty.</span><span class="sxs-lookup"><span data-stu-id="d201c-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="d201c-170">W przypadkach, gdy tablica przekazywana jest znana jako wielowymiarowa, można edytować kod języka pośredniego firmy Microsoft (MSIL) wyprodukowany przez Tlbimp.exe, a następnie ponownie go skompilować.</span><span class="sxs-lookup"><span data-stu-id="d201c-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="d201c-171">Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz [Dostosowywanie otoki wywoławcze środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d201c-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="d201c-172">Tablice w stylu C</span><span class="sxs-lookup"><span data-stu-id="d201c-172">C-Style Arrays</span></span>  
 <span data-ttu-id="d201c-173">Gdy tablica w stylu C jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="d201c-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="d201c-174">Typ elementu tablicy jest określany z biblioteki typów i zachowywany podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="d201c-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="d201c-175">Te same reguły konwersji, które mają zastosowanie do parametrów, mają również zastosowanie do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="d201c-176">Na przykład tablica typów **LPStr** staje się tablicą typów **string.**</span><span class="sxs-lookup"><span data-stu-id="d201c-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="d201c-177">Program Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do parametru.</span><span class="sxs-lookup"><span data-stu-id="d201c-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="d201c-178">Przyjmuje się, że ranga tablicy jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="d201c-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="d201c-179">Jeśli ranga jest większa niż 1, tablica jest organizowana jako tablica jednowymiarowa w kolejności głównej kolumny.</span><span class="sxs-lookup"><span data-stu-id="d201c-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="d201c-180">Dolna granica zawsze jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="d201c-181">Biblioteki typów mogą zawierać tablice o stałej lub zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="d201c-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="d201c-182">Program Tlbimp.exe może importować tylko tablice o stałej długości z bibliotek typów, ponieważ biblioteki typów nie są w stanie zorganizować tablic o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="d201c-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="d201c-183">W przypadku tablic o stałej długości rozmiar jest importowany z biblioteki typów i przechwytywany w naliczanym pliku **MarshalAsAttribute,** który jest stosowany do parametru.</span><span class="sxs-lookup"><span data-stu-id="d201c-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="d201c-184">Należy ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d201c-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="d201c-185">**Podpis niezarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-185">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="d201c-186">**Podpis zarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-186">**Managed signature**</span></span>  
  
```vb  
Sub New1(<MarshalAs(UnmanagedType.LPArray, SizeConst=10)> _  
   ar() As Integer)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, SizeConst=200)> _  
   ar() As Double)  
Sub New2(<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)> _  
   ar() As String)  
```  
  
```csharp  
void New1([MarshalAs(UnmanagedType.LPArray, SizeConst=10)] int[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray, SizeConst=200)] double[] ar);  
void New2([MarshalAs(UnmanagedType.LPArray,
   ArraySubType=UnmanagedType.LPWStr, SizeConst=10)] String[] ar);  
```  
  
 <span data-ttu-id="d201c-187">Chociaż można zastosować **size_is** lub **length_is** atrybuty do tablicy w źródle języka IDL (Interface Definition Language) w celu przekazania rozmiaru do klienta, kompilator języka MIDL (Microsoft Interface Definition Language) nie propaguje tych informacji do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="d201c-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="d201c-188">Nie znając rozmiaru usługi międzyoperacyjnej marshaling nie można marshal elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="d201c-189">W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania.</span><span class="sxs-lookup"><span data-stu-id="d201c-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="d201c-190">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-190">For example:</span></span>  
  
 <span data-ttu-id="d201c-191">**Podpis niezarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-191">**Unmanaged signature**</span></span>  
  
```cpp
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="d201c-192">**Podpis zarządzany**</span><span class="sxs-lookup"><span data-stu-id="d201c-192">**Managed signature**</span></span>  
  
```vb  
Sub New1(ByRef ar As Integer)  
Sub New2(ByRef ar As Double)  
Sub New3(ByRef ar As String)  
```  
  
```csharp  
void New1(ref int ar);
void New2(ref double ar);
void New3(ref String ar);
```  
  
 <span data-ttu-id="d201c-193">Organizatora można podać rozmiar tablicy, edytując kod języka pośredniego firmy Microsoft (MSIL) wyprodukowany przez program Tlbimp.exe, a następnie ponownie go kompilując.</span><span class="sxs-lookup"><span data-stu-id="d201c-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="d201c-194">Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz [Dostosowywanie otoki wywoławcze środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="d201c-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="d201c-195">Aby wskazać liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> ten typ do parametru tablicy definicji metody zarządzanej w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="d201c-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="d201c-196">Zidentyfikuj inny parametr, który zawiera liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="d201c-197">Parametry są identyfikowane przez położenie, począwszy od pierwszego parametru jako liczba 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>
  
    ```vb  
    Sub [New](ElemCnt As Integer, _  
       \<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       int ElemCnt,
       [MarshalAs(UnmanagedType.LPArray, SizeParamIndex=0)] int[] ar );  
    ```  
  
- <span data-ttu-id="d201c-198">Zdefiniuj rozmiar tablicy jako stałą.</span><span class="sxs-lookup"><span data-stu-id="d201c-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="d201c-199">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="d201c-200">Podczas organizowania tablic z kodu niezarządzanego do kodu zarządzanego, organizator sprawdza **MarshalAsAttribute skojarzone** z parametrem, aby określić rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="d201c-201">Jeśli rozmiar tablicy nie jest określony, tylko jeden element jest organizowane.</span><span class="sxs-lookup"><span data-stu-id="d201c-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d201c-202">**MarshalAsAttribute** nie ma wpływu na kierowanie tablice zarządzane do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d201c-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="d201c-203">W tym kierunku rozmiar tablicy jest określany przez badanie.</span><span class="sxs-lookup"><span data-stu-id="d201c-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="d201c-204">Nie ma sposobu, aby zorganizować podzbiór tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d201c-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="d201c-205">Organizator interop używa **CoTaskMemAlloc** i **CoTaskMemFree** metody alokacji i pobierania pamięci.</span><span class="sxs-lookup"><span data-stu-id="d201c-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="d201c-206">Alokacja pamięci wykonywane przez kod niezarządzany musi również korzystać z tych metod.</span><span class="sxs-lookup"><span data-stu-id="d201c-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="d201c-207">Przekazywanie tablic do com</span><span class="sxs-lookup"><span data-stu-id="d201c-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="d201c-208">Wszystkie typy tablic zarządzanych mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="d201c-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="d201c-209">W zależności od typu zarządzanego i atrybutów zastosowanych do niego, tablica jest dostępna jako tablica bezpieczna lub tablica w stylu C, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="d201c-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="d201c-210">Typ tablicy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="d201c-210">Managed array type</span></span>|<span data-ttu-id="d201c-211">Wywiezione jako</span><span class="sxs-lookup"><span data-stu-id="d201c-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="d201c-212">**\<** *type* Typ **ELEMENT_TYPE_SZARRAY\*\*\*\*>**</span><span class="sxs-lookup"><span data-stu-id="d201c-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="d201c-213"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="d201c-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d201c-214">**NiezarządzaneType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="d201c-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="d201c-215">Typ znajduje się w podpisie.</span><span class="sxs-lookup"><span data-stu-id="d201c-215">Type is provided in the signature.</span></span> <span data-ttu-id="d201c-216">Ranga jest zawsze 1, dolna granica jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="d201c-217">Rozmiar jest zawsze znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d201c-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="d201c-218">**\<** **ELEMENT_TYPE_ARRAY** **\<** **>** **\<** *ranga* *type* **>** typu [ *granice* **>**]</span><span class="sxs-lookup"><span data-stu-id="d201c-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="d201c-219">**NiezarządzaneType.SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="d201c-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d201c-220">**NiezarządzaneType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="d201c-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="d201c-221">Typ, ranga, granice są podane w podpisie.</span><span class="sxs-lookup"><span data-stu-id="d201c-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="d201c-222">Rozmiar jest zawsze znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d201c-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="d201c-223">**ELEMENT_TYPE_CLASS\*\*\*\*\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="d201c-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="d201c-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="d201c-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="d201c-225">**NiezarządzaneType.SafeArray(** *typ* **)**</span><span class="sxs-lookup"><span data-stu-id="d201c-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="d201c-226">Typ, ranga, granice i rozmiar są zawsze znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d201c-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="d201c-227">Istnieje ograniczenie w automatyzacji OLE odnoszące się do tablic struktur, które zawierają LPSTR lub LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="d201c-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="d201c-228">W związku z tym pola **ciąg** musi być zorganizowany jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="d201c-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="d201c-229">W przeciwnym razie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="d201c-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="d201c-230">Element_type_szarray</span><span class="sxs-lookup"><span data-stu-id="d201c-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="d201c-231">Gdy metoda zawierająca parametr **ELEMENT_TYPE_SZARRAY** (tablica jednowymiarowa) jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="d201c-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="d201c-232">Te same reguły konwersji mają zastosowanie do typów elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="d201c-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="d201c-233">Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do **safearray**.</span><span class="sxs-lookup"><span data-stu-id="d201c-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="d201c-234">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-235">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d201c-236">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-236">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="d201c-237">Ranga bezpiecznych tablic jest zawsze 1, a dolna granica jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="d201c-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="d201c-238">Rozmiar jest określany w czasie wykonywania przez rozmiar zarządzanej tablicy przekazywanych.</span><span class="sxs-lookup"><span data-stu-id="d201c-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="d201c-239">Tablica może być również organizowane jako tablicy <xref:System.Runtime.InteropServices.MarshalAsAttribute> w stylu C przy użyciu atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d201c-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d201c-240">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-241">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-241">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As Long, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPArray, _  
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar() As String, size as Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   long [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, SizeParamIndex=1)]
   String [] ar, int size );  
void New([MarshalAs(UnmanagedType.LPArray, ArraySubType=
   UnmanagedType.LPStr, SizeParamIndex=1)]
   String [] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d201c-242">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-242">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(BSTR ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="d201c-243">Chociaż organizator ma informacje o długości potrzebne do organizowania tablicy, długość tablicy jest zwykle przekazywana jako oddzielny argument do przekazywania długości do wywoływanego.</span><span class="sxs-lookup"><span data-stu-id="d201c-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="d201c-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="d201c-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="d201c-245">Gdy metoda zawierająca parametr **ELEMENT_TYPE_ARRAY** jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="d201c-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="d201c-246">Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do **safearray**.</span><span class="sxs-lookup"><span data-stu-id="d201c-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="d201c-247">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-248">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d201c-249">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-249">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] SAFEARRAY( long ) ar);
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="d201c-250">Ranga, rozmiar i granice tablic bezpieczeństwa są określane w czasie wykonywania przez właściwości tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="d201c-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="d201c-251">Tablica może być również organizowane jako tablicy <xref:System.Runtime.InteropServices.MarshalAsAttribute> w stylu C, stosując atrybut.</span><span class="sxs-lookup"><span data-stu-id="d201c-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d201c-252">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-253">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-253">Managed signature</span></span>  
  
```vb  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex:=1)> _  
   ar(,) As Long, size As Integer)  
Sub [New](<MarshalAs(UnmanagedType.LPARRAY, _  
   ArraySubType:=UnmanagedType.LPStr, SizeParamIndex:=1)> _  
   ar(,) As String, size As Integer)  
```  
  
```csharp  
void New([MarshalAs(UnmanagedType.LPARRAY, SizeParamIndex=1)]
   long [,] ar, int size );  
void New([MarshalAs(UnmanagedType.LPARRAY,
   ArraySubType= UnmanagedType.LPStr, SizeParamIndex=1)]
   String [,] ar, int size );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d201c-254">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-254">Unmanaged signature</span></span>  
  
```cpp
HRESULT New(long ar[]);
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="d201c-255">Tablice zagnieżdżone nie mogą być organizowane.</span><span class="sxs-lookup"><span data-stu-id="d201c-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="d201c-256">Na przykład następujący podpis generuje błąd podczas eksportowania z [eksporterem biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="d201c-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-257">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="d201c-258">> \<ELEMENT_TYPE_CLASS System.Array</span><span class="sxs-lookup"><span data-stu-id="d201c-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="d201c-259">Gdy metoda zawierająca <xref:System.Array?displayProperty=nameWithType> parametr jest eksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na interfejs **_Array.**</span><span class="sxs-lookup"><span data-stu-id="d201c-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="d201c-260">Zawartość tablicy zarządzanej są dostępne tylko za pośrednictwem metod i właściwości interfejsu **_Array.**</span><span class="sxs-lookup"><span data-stu-id="d201c-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="d201c-261">**System.Array** może być również organizowane jako **SAFEARRAY** przy użyciu atrybutu. <xref:System.Runtime.InteropServices.MarshalAsAttribute></span><span class="sxs-lookup"><span data-stu-id="d201c-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="d201c-262">Gdy organizowane jako bezpieczne tablicy, elementy tablicy są organizowane jako warianty.</span><span class="sxs-lookup"><span data-stu-id="d201c-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="d201c-263">Przykład:</span><span class="sxs-lookup"><span data-stu-id="d201c-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="d201c-264">Podpis zarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="d201c-265">Podpis niezarządzany</span><span class="sxs-lookup"><span data-stu-id="d201c-265">Unmanaged signature</span></span>  
  
```cpp
HRESULT New([in] _Array *ar);
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="d201c-266">Tablice w strukturach</span><span class="sxs-lookup"><span data-stu-id="d201c-266">Arrays within Structures</span></span>  
 <span data-ttu-id="d201c-267">Struktury niezarządzane mogą zawierać tablice osadzone.</span><span class="sxs-lookup"><span data-stu-id="d201c-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="d201c-268">Domyślnie te osadzone pola tablicy są organizowane jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="d201c-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="d201c-269">W poniższym `s1` przykładzie jest osadzona tablica, która jest przydzielana bezpośrednio w samej strukturze.</span><span class="sxs-lookup"><span data-stu-id="d201c-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="d201c-270">Reprezentacja niezarządzana</span><span class="sxs-lookup"><span data-stu-id="d201c-270">Unmanaged representation</span></span>  
  
```cpp
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="d201c-271">Tablice mogą być <xref:System.Runtime.InteropServices.UnmanagedType>organizowane jako , <xref:System.Runtime.InteropServices.MarshalAsAttribute> co wymaga, aby ustawić pole.</span><span class="sxs-lookup"><span data-stu-id="d201c-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="d201c-272">Rozmiar można ustawić tylko jako stałą.</span><span class="sxs-lookup"><span data-stu-id="d201c-272">The size can be set only as a constant.</span></span> <span data-ttu-id="d201c-273">Poniższy kod przedstawia odpowiednią `MyStruct`zarządzał definicję .</span><span class="sxs-lookup"><span data-stu-id="d201c-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
```vb  
Public Structure <StructLayout(LayoutKind.Sequential)> MyStruct  
   Public <MarshalAs(UnmanagedType.ByValArray, SizeConst := 128)> _  
     s1() As Short  
End Structure  
```  
  
```csharp  
[StructLayout(LayoutKind.Sequential)]  
public struct MyStruct {  
   [MarshalAs(UnmanagedType.ByValArray, SizeConst=128)] public short[] s1;  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="d201c-274">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d201c-274">See also</span></span>

- [<span data-ttu-id="d201c-275">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="d201c-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="d201c-276">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="d201c-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="d201c-277">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="d201c-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="d201c-278">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="d201c-278">Copying and Pinning</span></span>](copying-and-pinning.md)
