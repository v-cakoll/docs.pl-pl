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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 269d3b9ae5eec4412540b9b659cb287b3d26a482
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69946705"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="0150e-102">Organizowanie domyślne dotyczące tablic</span><span class="sxs-lookup"><span data-stu-id="0150e-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="0150e-103">W aplikacji składającej się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablicy jako parametry wejściowe/out.</span><span class="sxs-lookup"><span data-stu-id="0150e-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="0150e-104">W przeciwieństwie do organizatora międzyoperacyjności domyślnie przekazuje tablicę w postaci parametrów.</span><span class="sxs-lookup"><span data-stu-id="0150e-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="0150e-105">Dzięki [przypinaniu optymalizacji](copying-and-pinning.md)Tablica danych kopiowalnych może być wyświetlana jako parametr in/out podczas korzystania z obiektów w tym samym elemencie Apartment.</span><span class="sxs-lookup"><span data-stu-id="0150e-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="0150e-106">Jednak w przypadku późniejszego wyeksportowania kodu do biblioteki typów użytej do wygenerowania serwera proxy międzymaszynowego, a ta biblioteka jest używana do organizowania wywołań w ramach apartamentach, wywołania mogą przywrócić wartość true w zachowaniu parametrów.</span><span class="sxs-lookup"><span data-stu-id="0150e-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="0150e-107">Tablice są złożone z natury, a różnice między zarządzanymi i niezarządzanymi tablicami gwarantują więcej informacji niż w przypadku innych typów innych niż danych kopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="0150e-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="0150e-108">Zarządzane tablice</span><span class="sxs-lookup"><span data-stu-id="0150e-108">Managed Arrays</span></span>  
 <span data-ttu-id="0150e-109">Zarządzane typy tablic mogą się różnić; <xref:System.Array?displayProperty=nameWithType> jednak Klasa jest klasą bazową wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="0150e-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="0150e-110">Klasa **System. Array** ma właściwości do określania rangi, długości i dolnych i górnych granic tablicy, a także metod uzyskiwania dostępu do, sortowania, wyszukiwania, kopiowania i tworzenia tablic.</span><span class="sxs-lookup"><span data-stu-id="0150e-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="0150e-111">Te typy tablic są dynamiczne i nie mają odpowiedniego typu statycznego zdefiniowanego w bibliotece klas bazowych.</span><span class="sxs-lookup"><span data-stu-id="0150e-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="0150e-112">Wygodnie jest myśleć o każdej kombinacji typu elementu i rangi jako odrębny typ tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="0150e-113">W związku z tym, Jednowymiarowa tablica liczb całkowitych jest innego typu niż Jednowymiarowa tablica podwójnych typów.</span><span class="sxs-lookup"><span data-stu-id="0150e-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="0150e-114">Podobnie Dwuwymiarowa tablica liczb całkowitych różni się od jednowymiarowej tablicy liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0150e-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="0150e-115">Granice tablicy nie są brane pod uwagę podczas porównywania typów.</span><span class="sxs-lookup"><span data-stu-id="0150e-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="0150e-116">Jak przedstawiono w poniższej tabeli, każde wystąpienie tablicy zarządzanej musi mieć określony typ elementu, rangę i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="0150e-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="0150e-117">Typ tablicy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="0150e-117">Managed array type</span></span>|<span data-ttu-id="0150e-118">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="0150e-118">Element type</span></span>|<span data-ttu-id="0150e-119">Ranga</span><span class="sxs-lookup"><span data-stu-id="0150e-119">Rank</span></span>|<span data-ttu-id="0150e-120">Dolna granica</span><span class="sxs-lookup"><span data-stu-id="0150e-120">Lower bound</span></span>|<span data-ttu-id="0150e-121">Notacja podpisu</span><span class="sxs-lookup"><span data-stu-id="0150e-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="0150e-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="0150e-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="0150e-123">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="0150e-123">Specified by type.</span></span>|<span data-ttu-id="0150e-124">Określone przez rangę.</span><span class="sxs-lookup"><span data-stu-id="0150e-124">Specified by rank.</span></span>|<span data-ttu-id="0150e-125">Opcjonalnie określone przez granice.</span><span class="sxs-lookup"><span data-stu-id="0150e-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="0150e-126">*Typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="0150e-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="0150e-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="0150e-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="0150e-128">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0150e-128">Unknown</span></span>|<span data-ttu-id="0150e-129">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0150e-129">Unknown</span></span>|<span data-ttu-id="0150e-130">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0150e-130">Unknown</span></span>|<span data-ttu-id="0150e-131">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="0150e-131">**System.Array**</span></span>|  
|<span data-ttu-id="0150e-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="0150e-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="0150e-133">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="0150e-133">Specified by type.</span></span>|<span data-ttu-id="0150e-134">1</span><span class="sxs-lookup"><span data-stu-id="0150e-134">1</span></span>|<span data-ttu-id="0150e-135">0</span><span class="sxs-lookup"><span data-stu-id="0150e-135">0</span></span>|<span data-ttu-id="0150e-136">*Typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="0150e-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="0150e-137">Tablice niezarządzane</span><span class="sxs-lookup"><span data-stu-id="0150e-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="0150e-138">Tablice niezarządzane są tablicami bezpiecznymi w stylu COM lub tablicami w stylu C ze stałą lub zmienną długością.</span><span class="sxs-lookup"><span data-stu-id="0150e-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="0150e-139">Bezpieczne tablice to samoopisujące się tablice, które zawierają typ, rangę i granice skojarzonych danych tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="0150e-140">Tablice w stylu C to jednowymiarowe tablice z ustaloną dolną granicą 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="0150e-141">Usługa Marshaling ma ograniczoną obsługę obu typów tablic.</span><span class="sxs-lookup"><span data-stu-id="0150e-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="0150e-142">Przekazywanie parametrów tablicy do kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0150e-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="0150e-143">Zarówno tablice w stylu C, jak i bezpieczne tablice można przesłać do kodu platformy .NET z niezarządzanego kodu jako tablicę bezpieczną lub tablicę w stylu języka C.</span><span class="sxs-lookup"><span data-stu-id="0150e-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="0150e-144">W poniższej tabeli przedstawiono wartość typu niezarządzanego i typ zaimportowany.</span><span class="sxs-lookup"><span data-stu-id="0150e-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="0150e-145">Typ niezarządzany</span><span class="sxs-lookup"><span data-stu-id="0150e-145">Unmanaged type</span></span>|<span data-ttu-id="0150e-146">Typ zaimportowany</span><span class="sxs-lookup"><span data-stu-id="0150e-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="0150e-147">**SAFEARRAY (** *Typ* **)**</span><span class="sxs-lookup"><span data-stu-id="0150e-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="0150e-148">**ELEMENT_TYPE_SZARRAY** **\<** Przekonwertowanetype **>**</span><span class="sxs-lookup"><span data-stu-id="0150e-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="0150e-149">Ranga = 1, Dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="0150e-150">Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0150e-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="0150e-151">Tablic bezpiecznych, które nie mają rangi = 1 lub dolnego powiązania = 0, nie mogą być organizowane jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0150e-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="0150e-152">*Typ* **]**</span><span class="sxs-lookup"><span data-stu-id="0150e-152">*Type*  **[]**</span></span>|<span data-ttu-id="0150e-153">**ELEMENT_TYPE_SZARRAY** **\<** Przekonwertowanetype **>**</span><span class="sxs-lookup"><span data-stu-id="0150e-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="0150e-154">Ranga = 1, Dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="0150e-155">Rozmiar jest znany tylko wtedy, gdy jest podany w podpisie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0150e-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="0150e-156">Bezpieczne tablice</span><span class="sxs-lookup"><span data-stu-id="0150e-156">Safe Arrays</span></span>  
 <span data-ttu-id="0150e-157">Gdy bezpieczna tablica jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na tablicę jednowymiarową znanego typu (na przykład **int**).</span><span class="sxs-lookup"><span data-stu-id="0150e-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="0150e-158">Te same reguły konwersji typów, które mają zastosowanie do parametrów, mają zastosowanie także do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="0150e-159">Na przykład bezpieczna tablica typów **BSTR** jest zarządzaną tablicą ciągów, a bezpieczna tablica wariantów jest zarządzaną tablicą obiektów.</span><span class="sxs-lookup"><span data-stu-id="0150e-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="0150e-160">Typ elementu **SAFEARRAY** jest przechwytywany z biblioteki typów i zapisywany w <xref:System.Runtime.InteropServices.UnmanagedType> wartości **SAFEARRAY** wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0150e-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="0150e-161">Ponieważ ranga i granice tablicy bezpiecznej nie można ustalić na podstawie biblioteki typów, przyjmuje się, że ranga jest równa 1, a dolna granica jest przyjmowana jako równa 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="0150e-162">Ranga i granice muszą być zdefiniowane w zarządzanym podpisie wygenerowanym przez [importera biblioteki typów (Tlbimp. exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="0150e-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="0150e-163">Jeśli ranga przeniesiona do metody w czasie wykonywania różni się od <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> , jest generowany.</span><span class="sxs-lookup"><span data-stu-id="0150e-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="0150e-164">Jeśli typ tablicy przeszedł w czasie wykonywania różni się, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> zostanie zgłoszony.</span><span class="sxs-lookup"><span data-stu-id="0150e-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="0150e-165">W poniższym przykładzie przedstawiono bezpieczne tablice w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0150e-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="0150e-166">**Niezarządzany podpis**</span><span class="sxs-lookup"><span data-stu-id="0150e-166">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="0150e-167">**Sygnatura zarządzana**</span><span class="sxs-lookup"><span data-stu-id="0150e-167">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0150e-168">Wielowymiarowe lub niezerowe powiązane tablice mogą być organizowane w kodzie zarządzanym, jeśli sygnatura metody utworzona przez Tlbimp. exe została zmodyfikowana w celu wskazania typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0150e-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="0150e-169">Alternatywnie można użyć przełącznika **/sysarray** z Tlbimp. exe, aby zaimportować wszystkie tablice jako <xref:System.Array?displayProperty=nameWithType> obiekty.</span><span class="sxs-lookup"><span data-stu-id="0150e-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="0150e-170">W przypadku, gdy przenoszona tablica jest nazywana wielowymiarową, można edytować kod języka pośredniego firmy Microsoft (MSIL) utworzony przez Tlbimp. exe, a następnie ponownie go skompilować.</span><span class="sxs-lookup"><span data-stu-id="0150e-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="0150e-171">Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz Dostosowywanie wywoływanych [otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0150e-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="0150e-172">Tablice w stylu języka C</span><span class="sxs-lookup"><span data-stu-id="0150e-172">C-Style Arrays</span></span>  
 <span data-ttu-id="0150e-173">Gdy tablica w stylu C jest importowana z biblioteki typów do zestawu .NET, tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0150e-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="0150e-174">Typ elementu tablicy jest określany na podstawie biblioteki typów i zachowywany podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="0150e-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="0150e-175">Te same reguły konwersji, które mają zastosowanie do parametrów, mają zastosowanie także do elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="0150e-176">Na przykład Tablica typów **LPSTR** jest tablicą typów **ciągów** .</span><span class="sxs-lookup"><span data-stu-id="0150e-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="0150e-177">Tlbimp. exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut do parametru.</span><span class="sxs-lookup"><span data-stu-id="0150e-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="0150e-178">Przyjmuje się, że ranga tablicy jest równa 1.</span><span class="sxs-lookup"><span data-stu-id="0150e-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="0150e-179">Jeśli ranga jest większa niż 1, tablica jest organizowana jako tablica Jednowymiarowa w kolejności kolumny — główna.</span><span class="sxs-lookup"><span data-stu-id="0150e-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="0150e-180">Dolna granica zawsze jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="0150e-181">Biblioteki typów mogą zawierać tablice o stałej lub zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="0150e-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="0150e-182">Tlbimp. exe może importować tylko tablice o stałej długości z bibliotek typów, ponieważ biblioteki typów nie zawierają informacji wymaganych do organizowania tablic o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="0150e-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="0150e-183">W przypadku tablic o stałej długości rozmiar jest zaimportowany z biblioteki typów i przechwytywany w elemencie MarshalAsAttribute, który jest stosowany do parametru.</span><span class="sxs-lookup"><span data-stu-id="0150e-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="0150e-184">Należy ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0150e-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0150e-185">**Niezarządzany podpis**</span><span class="sxs-lookup"><span data-stu-id="0150e-185">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="0150e-186">**Sygnatura zarządzana**</span><span class="sxs-lookup"><span data-stu-id="0150e-186">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0150e-187">Chociaż atrybuty **size_is** lub **length_is** można zastosować do tablicy źródła w języku definicji interfejsu (IDL), aby przekazać rozmiar do klienta, kompilator Microsoft Interface Definition Language (MIDL) nie propaguje tego informacje do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="0150e-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="0150e-188">Bez znajomości rozmiaru usługa Marshaling Interop nie może zorganizować elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="0150e-189">W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania.</span><span class="sxs-lookup"><span data-stu-id="0150e-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="0150e-190">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-190">For example:</span></span>  
  
 <span data-ttu-id="0150e-191">**Niezarządzany podpis**</span><span class="sxs-lookup"><span data-stu-id="0150e-191">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="0150e-192">**Sygnatura zarządzana**</span><span class="sxs-lookup"><span data-stu-id="0150e-192">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0150e-193">Można przekazać Organizatorowi rozmiar tablicy, edytując kod języka pośredniego firmy Microsoft (MSIL) utworzony przez Tlbimp. exe, a następnie ponownie go skompilować.</span><span class="sxs-lookup"><span data-stu-id="0150e-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="0150e-194">Aby uzyskać szczegółowe informacje na temat modyfikowania kodu MSIL, zobacz Dostosowywanie wywoływanych [otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0150e-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="0150e-195">Aby wskazać liczbę elementów w tablicy, Zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ do parametru array definicji metody zarządzanej w jeden z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="0150e-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="0150e-196">Zidentyfikuj inny parametr zawierający liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="0150e-197">Parametry są identyfikowane według pozycji, rozpoczynając od pierwszego parametru jako numer 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
- <span data-ttu-id="0150e-198">Zdefiniuj rozmiar tablicy jako stałą.</span><span class="sxs-lookup"><span data-stu-id="0150e-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="0150e-199">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="0150e-200">Podczas organizowania tablic z niezarządzanego kodu do kodu zarządzanego Organizator sprawdza, czy atrybut **MarshalAsAttribute** skojarzony z parametrem, aby określić rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="0150e-201">Jeśli rozmiar tablicy nie zostanie określony, tylko jeden element jest zorganizowany.</span><span class="sxs-lookup"><span data-stu-id="0150e-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0150e-202">Wartość **MarshalAsAttribute** nie ma wpływu na kierowanie tablic zarządzanych do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0150e-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="0150e-203">W tym kierunku rozmiar tablicy jest określany przez badanie.</span><span class="sxs-lookup"><span data-stu-id="0150e-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="0150e-204">Nie istnieje sposób organizowania podzestawu zarządzanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="0150e-205">Organizator międzyoperacyjny używa metod **CoTaskMemAlloc** i **CoTaskMemFree** do przydzielania i pobierania pamięci.</span><span class="sxs-lookup"><span data-stu-id="0150e-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="0150e-206">Alokacja pamięci wykonywana przez kod niezarządzany również musi używać tych metod.</span><span class="sxs-lookup"><span data-stu-id="0150e-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="0150e-207">Przekazywanie tablic do modelu COM</span><span class="sxs-lookup"><span data-stu-id="0150e-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="0150e-208">Wszystkie typy tablicy zarządzanej mogą być przesyłane do niezarządzanego kodu z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0150e-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="0150e-209">W zależności od typu zarządzanego i zastosowanych do niego atrybutów tablica może być dostępna jako bezpieczna tablica lub tablica w stylu C, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0150e-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0150e-210">Typ tablicy zarządzanej</span><span class="sxs-lookup"><span data-stu-id="0150e-210">Managed array type</span></span>|<span data-ttu-id="0150e-211">Wyeksportowany jako</span><span class="sxs-lookup"><span data-stu-id="0150e-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="0150e-212">**ELEMENT_TYPE_SZARRAY** **\<** *Typ* **>**</span><span class="sxs-lookup"><span data-stu-id="0150e-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="0150e-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="0150e-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0150e-214">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="0150e-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="0150e-215">Typ jest podany w podpisie.</span><span class="sxs-lookup"><span data-stu-id="0150e-215">Type is provided in the signature.</span></span> <span data-ttu-id="0150e-216">Ranga jest zawsze 1, Dolna granica jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="0150e-217">Rozmiar jest zawsze znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0150e-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="0150e-218">**ELEMENT_TYPE_ARRAY** *ranga* **>** typu [ **Bounds>** ] **\<** **>** **\<** **\<**</span><span class="sxs-lookup"><span data-stu-id="0150e-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="0150e-219">**UnmanagedType. SAFEARRAY (** *Typ* **)**</span><span class="sxs-lookup"><span data-stu-id="0150e-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0150e-220">**UnmanagedType. LPArray**</span><span class="sxs-lookup"><span data-stu-id="0150e-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="0150e-221">Typ, ranga, granice są podane w podpisie.</span><span class="sxs-lookup"><span data-stu-id="0150e-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="0150e-222">Rozmiar jest zawsze znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0150e-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="0150e-223">**ELEMENT_TYPE_CLASS** **\<** <xref:System.Array?displayProperty=nameWithType> **>**</span><span class="sxs-lookup"><span data-stu-id="0150e-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="0150e-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="0150e-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="0150e-225">**UnmanagedType. SAFEARRAY (** *Typ* **)**</span><span class="sxs-lookup"><span data-stu-id="0150e-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0150e-226">Typ, ranga, granice i rozmiar są zawsze znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0150e-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="0150e-227">Istnieje ograniczenie dotyczące automatyzacji OLE odnoszące się do tablic struktur, które zawierają LPSTR lub LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="0150e-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="0150e-228">W związku z tym pola **String** muszą być organizowane jako UnmanagedType **. BSTR**.</span><span class="sxs-lookup"><span data-stu-id="0150e-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="0150e-229">W przeciwnym razie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0150e-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="element_type_szarray"></a><span data-ttu-id="0150e-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="0150e-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="0150e-231">Gdy metoda zawierająca parametr **ELEMENT_TYPE_SZARRAY** (tablica Jednowymiarowa) jest eksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na typ **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="0150e-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="0150e-232">Te same reguły konwersji mają zastosowanie do typów elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="0150e-233">Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do elementu **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0150e-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="0150e-234">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-235">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0150e-236">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="0150e-236">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="0150e-237">Ranga tablic bezpiecznych jest zawsze 1, a dolna granica jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="0150e-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="0150e-238">Rozmiar jest określany w czasie wykonywania przez rozmiar przesyłanej tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0150e-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="0150e-239">Tablica może być również organizowana jako tablica w stylu C przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0150e-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0150e-240">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-241">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-241">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0150e-242">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="0150e-242">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="0150e-243">Chociaż Organizator ma informacje o długości wymaganej do zorganizowania tablicy, Długość tablicy jest zwykle przekazywany jako oddzielny argument, aby przekazać długość do elementu wywoływanego.</span><span class="sxs-lookup"><span data-stu-id="0150e-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="element_type_array"></a><span data-ttu-id="0150e-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="0150e-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="0150e-245">Gdy metoda zawierająca parametr **ELEMENT_TYPE_ARRAY** jest eksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na typ **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="0150e-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="0150e-246">Zawartość tablicy zarządzanej jest automatycznie kopiowana z pamięci zarządzanej do elementu **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0150e-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="0150e-247">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-248">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0150e-249">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="0150e-249">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="0150e-250">Ranga, rozmiar i granice bezpiecznych tablic są określane w czasie wykonywania przez charakterystykę zarządzanej tablicy.</span><span class="sxs-lookup"><span data-stu-id="0150e-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="0150e-251">Tablica może być również organizowana jako tablica w stylu C przez zastosowanie <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0150e-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0150e-252">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-253">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-253">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0150e-254">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="0150e-254">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="0150e-255">Nie można zorganizować tablic zagnieżdżonych.</span><span class="sxs-lookup"><span data-stu-id="0150e-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="0150e-256">Na przykład następujący podpis generuje błąd podczas eksportowania z [eksporterem biblioteki typów (Tlbexp. exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="0150e-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-257">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="element_type_class-systemarray"></a><span data-ttu-id="0150e-258">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="0150e-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="0150e-259">Gdy metoda zawierająca <xref:System.Array?displayProperty=nameWithType> parametr zostanie wyeksportowana z zestawu .NET do biblioteki typów, parametr array jest konwertowany na interfejs **_Array** .</span><span class="sxs-lookup"><span data-stu-id="0150e-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="0150e-260">Zawartość tablicy zarządzanej jest dostępna tylko za pomocą metod i właściwości interfejsu **_Array** .</span><span class="sxs-lookup"><span data-stu-id="0150e-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="0150e-261">Element **System. Array** może być również zorganizowany jako **SAFEARRAY** przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0150e-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0150e-262">Gdy jest zorganizowany jako bezpieczna tablica, elementy tablicy są organizowane jako warianty.</span><span class="sxs-lookup"><span data-stu-id="0150e-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="0150e-263">Przykład:</span><span class="sxs-lookup"><span data-stu-id="0150e-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0150e-264">Sygnatura zarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0150e-265">Niezarządzany podpis</span><span class="sxs-lookup"><span data-stu-id="0150e-265">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="0150e-266">Tablice w strukturach</span><span class="sxs-lookup"><span data-stu-id="0150e-266">Arrays within Structures</span></span>  
 <span data-ttu-id="0150e-267">Struktury niezarządzane mogą zawierać osadzone tablice.</span><span class="sxs-lookup"><span data-stu-id="0150e-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="0150e-268">Domyślnie te osadzone pola tablicy są organizowane jako SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="0150e-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="0150e-269">W poniższym przykładzie `s1` jest osadzoną tablicą przydzieloną bezpośrednio w samej strukturze.</span><span class="sxs-lookup"><span data-stu-id="0150e-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="0150e-270">Reprezentacja niezarządzana</span><span class="sxs-lookup"><span data-stu-id="0150e-270">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="0150e-271">Tablice mogą być organizowane jako <xref:System.Runtime.InteropServices.UnmanagedType>, co wymaga <xref:System.Runtime.InteropServices.MarshalAsAttribute> ustawienia pola.</span><span class="sxs-lookup"><span data-stu-id="0150e-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="0150e-272">Rozmiar można ustawić tylko jako stała.</span><span class="sxs-lookup"><span data-stu-id="0150e-272">The size can be set only as a constant.</span></span> <span data-ttu-id="0150e-273">Poniższy kod pokazuje odpowiadającą zarządzane definicje `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="0150e-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0150e-274">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0150e-274">See also</span></span>

- [<span data-ttu-id="0150e-275">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="0150e-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="0150e-276">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="0150e-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="0150e-277">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0150e-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="0150e-278">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="0150e-278">Copying and Pinning</span></span>](copying-and-pinning.md)
