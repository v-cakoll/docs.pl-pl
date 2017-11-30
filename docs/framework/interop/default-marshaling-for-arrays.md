---
title: "Organizowanie domyślne dotyczące tablic"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- interop marshaling, arrays
- arrays, interop marshaling
ms.assetid: 8a3cca8b-dd94-4e3d-ad9a-9ee7590654bc
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: ab9a72607f5201164f31d9e4cfdf058e9af804ae
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="34634-102">Domyślny marshaling dla tablic</span><span class="sxs-lookup"><span data-stu-id="34634-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="34634-103">W aplikacji, składające się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="34634-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="34634-104">Z kolei międzyoperacyjnego organizatora przekazuje tablicy, tak jak parametry domyślnie.</span><span class="sxs-lookup"><span data-stu-id="34634-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="34634-105">Z [przypinania optymalizacji](../../../docs/framework/interop/copying-and-pinning.md), tablicy kopiowalne może występować działanie jako In/Out parametru podczas interakcji z obiektów w tym samym apartamencie.</span><span class="sxs-lookup"><span data-stu-id="34634-105">With [pinning optimization](../../../docs/framework/interop/copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="34634-106">Jeśli później wyeksportować kod do biblioteki typów, używany do generowania proxy między komputerami, a biblioteki jest używany do organizowania wywołania w apartamentach, wywołania można przywrócić na wartość true w zachowaniu parametru.</span><span class="sxs-lookup"><span data-stu-id="34634-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="34634-107">Tablice są skomplikowane natury, a różnice między zarządzanymi i niezarządzanymi macierzami gwarantuje więcej informacji od innych typów niekopiowalne.</span><span class="sxs-lookup"><span data-stu-id="34634-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span> <span data-ttu-id="34634-108">Ten temat zawiera następujące informacje na przekazywanie tablic:</span><span class="sxs-lookup"><span data-stu-id="34634-108">This topic provides the following information on marshaling arrays:</span></span>  
  
-   [<span data-ttu-id="34634-109">Tablice zarządzane</span><span class="sxs-lookup"><span data-stu-id="34634-109">Managed Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor1)  
  
-   [<span data-ttu-id="34634-110">Tablice niezarządzane</span><span class="sxs-lookup"><span data-stu-id="34634-110">Unmanaged Arrays</span></span>](#cpcondefaultmarshalingforarraysanchor2)  
  
-   [<span data-ttu-id="34634-111">Przekazywanie parametrów tablicy do kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="34634-111">Passing Array Parameters to .NET Code</span></span>](#cpcondefaultmarshalingforarraysanchor3)  
  
-   [<span data-ttu-id="34634-112">Przekazywanie tablic w modelu COM</span><span class="sxs-lookup"><span data-stu-id="34634-112">Passing Arrays to COM</span></span>](#cpcondefaultmarshalingforarraysanchor4)  
  
<a name="cpcondefaultmarshalingforarraysanchor1"></a>   
## <a name="managed-arrays"></a><span data-ttu-id="34634-113">Tablice zarządzane</span><span class="sxs-lookup"><span data-stu-id="34634-113">Managed Arrays</span></span>  
 <span data-ttu-id="34634-114">Zarządzane tablicy, która może różnić się typy; jednak <xref:System.Array?displayProperty=nameWithType> klasa jest klasą bazową dla wszystkich typów tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-114">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="34634-115">**System.Array** klasa ma właściwości określające rangę, długość i dolną i górną granicę tablicy, a także metod do uzyskiwania dostępu do, sortowanie, wyszukiwanie, kopiowanie i tworzenia tablic.</span><span class="sxs-lookup"><span data-stu-id="34634-115">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="34634-116">Typy tablicy są dynamiczne i nie mają odpowiednich typu statycznego zdefiniowany w klasie podstawowej biblioteki.</span><span class="sxs-lookup"><span data-stu-id="34634-116">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="34634-117">Jest wygodną Rozważmy każdej kombinacji typ elementu i rangę jako różne typu tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-117">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="34634-118">W związku z tym jest tablicą jednowymiarową liczb całkowitych jest innego typu niż tablicą jednowymiarową typu double.</span><span class="sxs-lookup"><span data-stu-id="34634-118">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="34634-119">Podobnie jest tablicą dwuwymiarową liczb całkowitych różni się od Jednowymiarowa tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="34634-119">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="34634-120">Granice tablicy nie są uwzględniane podczas porównywania typów.</span><span class="sxs-lookup"><span data-stu-id="34634-120">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="34634-121">Jak pokazano na poniższej tabeli, wszystkie wystąpienia tablicy musi być typ określonego elementu, Ranking i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="34634-121">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="34634-122">Typ tablicy zarządzanego</span><span class="sxs-lookup"><span data-stu-id="34634-122">Managed array type</span></span>|<span data-ttu-id="34634-123">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="34634-123">Element type</span></span>|<span data-ttu-id="34634-124">Ranga</span><span class="sxs-lookup"><span data-stu-id="34634-124">Rank</span></span>|<span data-ttu-id="34634-125">Dolna granica</span><span class="sxs-lookup"><span data-stu-id="34634-125">Lower bound</span></span>|<span data-ttu-id="34634-126">Notacja podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-126">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="34634-127">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="34634-127">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="34634-128">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="34634-128">Specified by type.</span></span>|<span data-ttu-id="34634-129">Określony przez rangę.</span><span class="sxs-lookup"><span data-stu-id="34634-129">Specified by rank.</span></span>|<span data-ttu-id="34634-130">Opcjonalnie określony przez granice.</span><span class="sxs-lookup"><span data-stu-id="34634-130">Optionally specified by bounds.</span></span>|<span data-ttu-id="34634-131">*Typ* **[**  *n* ,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="34634-131">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="34634-132">**PO ELEMENCIE ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="34634-132">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="34634-133">Nieznany</span><span class="sxs-lookup"><span data-stu-id="34634-133">Unknown</span></span>|<span data-ttu-id="34634-134">Nieznany</span><span class="sxs-lookup"><span data-stu-id="34634-134">Unknown</span></span>|<span data-ttu-id="34634-135">Nieznany</span><span class="sxs-lookup"><span data-stu-id="34634-135">Unknown</span></span>|<span data-ttu-id="34634-136">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="34634-136">**System.Array**</span></span>|  
|<span data-ttu-id="34634-137">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="34634-137">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="34634-138">Określony przez typ.</span><span class="sxs-lookup"><span data-stu-id="34634-138">Specified by type.</span></span>|<span data-ttu-id="34634-139">1</span><span class="sxs-lookup"><span data-stu-id="34634-139">1</span></span>|<span data-ttu-id="34634-140">0</span><span class="sxs-lookup"><span data-stu-id="34634-140">0</span></span>|<span data-ttu-id="34634-141">*Typ* **[**  *n*  **]**</span><span class="sxs-lookup"><span data-stu-id="34634-141">*type* **[** *n* **]**</span></span>|  
  
<a name="cpcondefaultmarshalingforarraysanchor2"></a>   
## <a name="unmanaged-arrays"></a><span data-ttu-id="34634-142">Tablice niezarządzane</span><span class="sxs-lookup"><span data-stu-id="34634-142">Unmanaged Arrays</span></span>  
 <span data-ttu-id="34634-143">Tablice niezarządzane są tablice bezpieczne styl modelu COM lub stylu języka C tablice o stałym rozmiarze lub zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="34634-143">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="34634-144">Tablice bezpieczne są samoopisujące tablic zawierających typu, Ranking i granice danych skojarzonej macierzy.</span><span class="sxs-lookup"><span data-stu-id="34634-144">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="34634-145">Tablice w stylu języka C są jednowymiarowe tablice o określonym typie ze stałym dolna granica 0.</span><span class="sxs-lookup"><span data-stu-id="34634-145">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="34634-146">Usługa kierowania ma ograniczony pomocy technicznej dla obu typów tablic.</span><span class="sxs-lookup"><span data-stu-id="34634-146">The marshaling service has limited support for both types of arrays.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor3"></a>   
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="34634-147">Przekazywanie parametrów tablicy do kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="34634-147">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="34634-148">Zarówno tablic w stylu języka C i bezpieczne tablice mogą być przekazywane do kodu platformy .NET z kodem niezarządzanym jako bezpiecznej tablicy lub tablica stylu języka C.</span><span class="sxs-lookup"><span data-stu-id="34634-148">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="34634-149">W poniższej tabeli przedstawiono wartości typu niezarządzanego i typu zaimportowanego.</span><span class="sxs-lookup"><span data-stu-id="34634-149">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="34634-150">Typ niezarządzany</span><span class="sxs-lookup"><span data-stu-id="34634-150">Unmanaged type</span></span>|<span data-ttu-id="34634-151">Zaimportowany typ</span><span class="sxs-lookup"><span data-stu-id="34634-151">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="34634-152">**SafeArray (** *typu* **)**</span><span class="sxs-lookup"><span data-stu-id="34634-152">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="34634-153">**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**</span><span class="sxs-lookup"><span data-stu-id="34634-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="34634-154">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="34634-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="34634-155">Rozmiar jest znany, tylko jeśli są dostępne w zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="34634-155">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="34634-156">Tablice bezpieczne, które nie są rangi = 1 lub dolna granica = 0, nie mogą być przekazywane jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="34634-156">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="34634-157">*Typ***]** </span><span class="sxs-lookup"><span data-stu-id="34634-157">*Type*  **[]**</span></span>|<span data-ttu-id="34634-158">**ELEMENT_TYPE_SZARRAY**  **\<**  *ConvertedType***>**</span><span class="sxs-lookup"><span data-stu-id="34634-158">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="34634-159">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="34634-159">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="34634-160">Rozmiar jest znany, tylko jeśli są dostępne w zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="34634-160">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="34634-161">Tablice bezpieczne</span><span class="sxs-lookup"><span data-stu-id="34634-161">Safe Arrays</span></span>  
 <span data-ttu-id="34634-162">Po zaimportowaniu bezpiecznej tablicy z biblioteki typów na zestaw .NET tablicy jest konwertowana na tablicą jednowymiarową znanego typu (takich jak **int**).</span><span class="sxs-lookup"><span data-stu-id="34634-162">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="34634-163">Tej samej reguły konwersji typów, które są stosowane do parametrów dotyczą również elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-163">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="34634-164">Na przykład bezpieczną tablicą o **BSTR** typy staje się tablicy ciągów i bezpieczną tablicą typu Variant staje się zarządzanych Tablica obiektów.</span><span class="sxs-lookup"><span data-stu-id="34634-164">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="34634-165">**SAFEARRAY** typ elementu zostaną zebrane z biblioteki typów i zapisywane w **SAFEARRAY** wartość <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="34634-165">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="34634-166">Ponieważ ranga i granice bezpiecznej tablicy nie można określić z biblioteki typów, rangę zakłada, że jest równa 1 oraz dolną granicę zakłada, że jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="34634-166">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="34634-167">Ranga i zakresem, musi być zdefiniowana w zarządzanego podpisu utworzonego przez [Importer biblioteki typów (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="34634-167">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../../../docs/framework/tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="34634-168">Jeśli różni się rangę przekazywany do metody w czasie wykonywania, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="34634-168">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="34634-169">Jeśli typ tablicy został przekazany w czasie wykonywania jest inny, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> jest generowany.</span><span class="sxs-lookup"><span data-stu-id="34634-169">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="34634-170">Poniższy przykład przedstawia tablice bezpieczne, zarządzane i niezarządzane kodu.</span><span class="sxs-lookup"><span data-stu-id="34634-170">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="34634-171">**Niezarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-171">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="34634-172">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-172">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="34634-173">Wielowymiarowym lub niezerowe granica tablic bezpieczne, można zorganizować kodu zarządzanego, jeśli podpis metody generowane przez Tlbimp.exe są modyfikowane w celu wskazywać typu elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_ TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="34634-173">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="34634-174">Alternatywnie można użyć **/sysarray** przełącznik z Tlbimp.exe Aby zaimportować wszystkie tablice jako <xref:System.Array?displayProperty=nameWithType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="34634-174">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="34634-175">W przypadkach, gdy tablica przekazywany jest znany jako wielowymiarowych możesz edytować wyprodukowanych kod języka pośredniego (MSIL) firmy Microsoft przez Tlbimp.exe i ponownie go skompilować.</span><span class="sxs-lookup"><span data-stu-id="34634-175">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="34634-176">Aby uzyskać szczegółowe informacje na temat sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływane otoki środowiska uruchomieniowego](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span><span class="sxs-lookup"><span data-stu-id="34634-176">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="34634-177">Tablice w stylu języka C</span><span class="sxs-lookup"><span data-stu-id="34634-177">C-Style Arrays</span></span>  
 <span data-ttu-id="34634-178">Po zaimportowaniu tablicy stylu języka C z biblioteki typów na zestaw .NET tablicy jest konwertowana na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="34634-178">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="34634-179">Typ elementu tablicy jest określana na podstawie biblioteki typów i zachowane podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="34634-179">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="34634-180">Tej samej reguły konwersji, które są stosowane do parametrów dotyczą również elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-180">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="34634-181">Na przykład tablicę **LPStr** typy staje się tablicę **ciąg** typów.</span><span class="sxs-lookup"><span data-stu-id="34634-181">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="34634-182">Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu parametru.</span><span class="sxs-lookup"><span data-stu-id="34634-182">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="34634-183">Ranga tablicy zakłada się, że równa 1.</span><span class="sxs-lookup"><span data-stu-id="34634-183">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="34634-184">Jeśli pozycja jest większa niż 1, tablicy jest przekazywane jako tablica jednowymiarowa w kolejności kolumn.</span><span class="sxs-lookup"><span data-stu-id="34634-184">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="34634-185">Dolna granica jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="34634-185">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="34634-186">Biblioteki typów mogą zawierać tablic o stałej lub zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="34634-186">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="34634-187">Tlbimp.exe można importować tylko o stałej długości tablic z biblioteki typów, ponieważ informacje wymagane do organizowania tablice o zmiennej długości brakuje biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="34634-187">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="34634-188">O stałej długości tablic, rozmiar jest zaimportowany z biblioteki typów i przechwytywane **atrybut MarshalAsAttribute** do parametru zastosowano.</span><span class="sxs-lookup"><span data-stu-id="34634-188">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="34634-189">Trzeba ręcznie zdefiniować typu biblioteki zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="34634-189">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="34634-190">**Niezarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-190">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="34634-191">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-191">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="34634-192">Mimo że można zastosować **size_is** lub **length_is —** atrybutów do tablicy w źródle języka definicji interfejsu (IDL) w celu przedstawienia rozmiar do klienta, języka definicji interfejsu firmy Microsoft (MIDL) Kompilator nie są propagowane tych informacji do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="34634-192">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="34634-193">Bez wiedzy o rozmiar, interop organizowanie usługi nie można zorganizować elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-193">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="34634-194">W rezultacie tablice o zmiennej długości są importowane jako argumenty odwołania.</span><span class="sxs-lookup"><span data-stu-id="34634-194">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="34634-195">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-195">For example:</span></span>  
  
 <span data-ttu-id="34634-196">**Niezarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-196">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="34634-197">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="34634-197">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="34634-198">Organizator można udostępnić w rozmiar tablicy, edytując kod języka pośredniego (MSIL) wyprodukowanych firmy Microsoft przez Tlbimp.exe i następnie ponownej kompilacji.</span><span class="sxs-lookup"><span data-stu-id="34634-198">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="34634-199">Aby uzyskać szczegółowe informacje na temat sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływane otoki środowiska uruchomieniowego](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span><span class="sxs-lookup"><span data-stu-id="34634-199">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](http://msdn.microsoft.com/en-us/4652beaf-77d0-4f37-9687-ca193288c0be).</span></span> <span data-ttu-id="34634-200">Wskaż liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> typu parametru tablicy definicji metody zarządzanego w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="34634-200">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
-   <span data-ttu-id="34634-201">Określ inny parametr, który zawiera liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-201">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="34634-202">Parametry są identyfikowane za pomocą pozycji, począwszy od pierwszego parametru jako liczba 0.</span><span class="sxs-lookup"><span data-stu-id="34634-202">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
-   <span data-ttu-id="34634-203">Zdefiniuj rozmiar tablicy jako stała.</span><span class="sxs-lookup"><span data-stu-id="34634-203">Define the size of the array as a constant.</span></span> <span data-ttu-id="34634-204">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-204">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="34634-205">Podczas organizowania tablic z kodem niezarządzanym do kodu zarządzanego, sprawdza organizatora **atrybut MarshalAsAttribute** skojarzonych z parametrem, aby określić rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-205">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="34634-206">Jeśli nie określono rozmiaru tablicy, zorganizować jest tylko jeden element.</span><span class="sxs-lookup"><span data-stu-id="34634-206">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="34634-207">**Atrybut MarshalAsAttribute** nie wpływa na przekazywanie zarządza tablic do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="34634-207">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="34634-208">W tym kierunku rozmiaru tablicy jest określana przez badania.</span><span class="sxs-lookup"><span data-stu-id="34634-208">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="34634-209">Nie istnieje sposób do organizowania podzbiór tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-209">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="34634-210">Organizator międzyoperacyjnego używa **CoTaskMemAlloc** i **CoTaskMemFree** metod można przydzielić i pobrać pamięci.</span><span class="sxs-lookup"><span data-stu-id="34634-210">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="34634-211">Alokacja pamięci wykonywane przez kod niezarządzany również użyć tych metod.</span><span class="sxs-lookup"><span data-stu-id="34634-211">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
<a name="cpcondefaultmarshalingforarraysanchor4"></a>   
## <a name="passing-arrays-to-com"></a><span data-ttu-id="34634-212">Przekazywanie tablic w modelu COM</span><span class="sxs-lookup"><span data-stu-id="34634-212">Passing Arrays to COM</span></span>  
 <span data-ttu-id="34634-213">Wszystkie typy tablicy mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="34634-213">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="34634-214">W zależności od typu zarządzanego i atrybuty tablicy są dostępne jako bezpiecznej tablicy lub tablica stylu języka C, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="34634-214">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="34634-215">Typ tablicy zarządzanego</span><span class="sxs-lookup"><span data-stu-id="34634-215">Managed array type</span></span>|<span data-ttu-id="34634-216">Wyeksportowany jako</span><span class="sxs-lookup"><span data-stu-id="34634-216">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="34634-217">**ELEMENT_TYPE_SZARRAY**  **\<**  *typu***>**</span><span class="sxs-lookup"><span data-stu-id="34634-217">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="34634-218"><xref:System.Runtime.InteropServices.UnmanagedType>**. SafeArray (** *typu* **)**</span><span class="sxs-lookup"><span data-stu-id="34634-218"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="34634-219">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="34634-219">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="34634-220">Typ jest dostępne w podpisie.</span><span class="sxs-lookup"><span data-stu-id="34634-220">Type is provided in the signature.</span></span> <span data-ttu-id="34634-221">Pozycja ma zawsze numer 1, dolna granica jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="34634-221">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="34634-222">Rozmiar zawsze jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34634-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="34634-223">**ELEMENT_TYPE_ARRAY**  **\<**  *typu*  **>**   **\<**  *rangę*  **>** [ **\<**  *granice*  **>** ]</span><span class="sxs-lookup"><span data-stu-id="34634-223">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="34634-224">**UnmanagedType.SafeArray (** *typu* **)**</span><span class="sxs-lookup"><span data-stu-id="34634-224">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="34634-225">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="34634-225">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="34634-226">Granice rangi, typ, znajdują się w podpisie.</span><span class="sxs-lookup"><span data-stu-id="34634-226">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="34634-227">Rozmiar zawsze jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34634-227">Size is always known at run time.</span></span>|  
|<span data-ttu-id="34634-228">**PO ELEMENCIE ELEMENT_TYPE_CLASS****\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="34634-228">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="34634-229">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="34634-229">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="34634-230">**UnmanagedType.SafeArray (** *typu* **)**</span><span class="sxs-lookup"><span data-stu-id="34634-230">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="34634-231">Typ, pozycja, granice i rozmiar zawsze są określane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="34634-231">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="34634-232">Istnieje ograniczenie w automatyzacji OLE odnoszących się do tablic struktury zawierające LPSTR lub LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="34634-232">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="34634-233">W związku z tym **ciąg** pola muszą być przekazywane jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="34634-233">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="34634-234">W przeciwnym razie zostanie wygenerowany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="34634-234">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="34634-235">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="34634-235">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="34634-236">Gdy metoda zawiera **ELEMENT_TYPE_SZARRAY** parametr (jednowymiarową) jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="34634-236">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="34634-237">Te same reguły konwersji dotyczą typ elementu tablicy.</span><span class="sxs-lookup"><span data-stu-id="34634-237">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="34634-238">Zawartość tablicy zarządzanej automatycznie są kopiowane z pamięci zarządzanej do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="34634-238">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="34634-239">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-239">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-240">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-240">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="34634-241">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-241">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="34634-242">Pozycja tablice bezpieczne ma zawsze numer 1 i dolną granicą jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="34634-242">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="34634-243">Rozmiar jest określany w czasie wykonywania przez rozmiar tablicy zarządzanej przekazywany.</span><span class="sxs-lookup"><span data-stu-id="34634-243">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="34634-244">Tablica można również zorganizować jako tablica stylu języka C za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="34634-244">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="34634-245">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-245">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-246">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-246">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="34634-247">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-247">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="34634-248">Mimo że organizator ma długość potrzebnych do organizowania tablicy, długość tablicy zwykle jest przekazywany jako osobne argumentu o długości do wywoływany.</span><span class="sxs-lookup"><span data-stu-id="34634-248">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="34634-249">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="34634-249">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="34634-250">Gdy metoda zawiera **ELEMENT_TYPE_ARRAY** parametru jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="34634-250">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="34634-251">Zawartość tablicy zarządzanej automatycznie są kopiowane z pamięci zarządzanej do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="34634-251">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="34634-252">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-253">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-253">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="34634-254">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-254">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="34634-255">Ranga, rozmiar i granice tablice bezpieczne są określane w czasie wykonywania przez właściwości tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="34634-255">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="34634-256">Tablica można również zorganizować jako tablica stylu języka C, stosując <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="34634-256">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="34634-257">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-257">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-258">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-258">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="34634-259">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-259">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="34634-260">Tablice zagnieżdżone nie mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="34634-260">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="34634-261">Na przykład następująca sygnatura generuje błąd podczas eksportowania z [Eksporter biblioteki typów (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="34634-261">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-262">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-262">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="34634-263">Po elemencie ELEMENT_TYPE_CLASS \<System.Array ></span><span class="sxs-lookup"><span data-stu-id="34634-263">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="34634-264">Gdy metoda zawiera <xref:System.Array?displayProperty=nameWithType> parametru jest wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowana na **_Array** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="34634-264">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="34634-265">Zawartość tablicy zarządzanej są dostępne tylko za pośrednictwem metody i właściwości **_Array** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="34634-265">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="34634-266">**System.Array** również mogą być przekazywane jako **SAFEARRAY** przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="34634-266">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="34634-267">Gdy przekazywane jako Tablica bezpieczna, elementy tablicy są przekazywane jako wariantów.</span><span class="sxs-lookup"><span data-stu-id="34634-267">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="34634-268">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="34634-268">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="34634-269">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-269">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="34634-270">Niezarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="34634-270">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="34634-271">Tablice w strukturach</span><span class="sxs-lookup"><span data-stu-id="34634-271">Arrays within Structures</span></span>  
 <span data-ttu-id="34634-272">Niezarządzane struktury może zawierać osadzone tablic.</span><span class="sxs-lookup"><span data-stu-id="34634-272">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="34634-273">Domyślnie te pola osadzonej tablicy są przekazywane jako obiektu SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="34634-273">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="34634-274">W poniższym przykładzie `s1` jest osadzoną tablicę, która jest przydzielane bezpośrednio w strukturze samej siebie.</span><span class="sxs-lookup"><span data-stu-id="34634-274">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="34634-275">Reprezentacja niezarządzane</span><span class="sxs-lookup"><span data-stu-id="34634-275">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="34634-276">Tablice mogą być przekazywane jako <xref:System.Runtime.InteropServices.UnmanagedType>, który wymaga ustawienia <xref:System.Runtime.InteropServices.MarshalAsAttribute> pola.</span><span class="sxs-lookup"><span data-stu-id="34634-276">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="34634-277">Rozmiar można ustawić tylko jako stała.</span><span class="sxs-lookup"><span data-stu-id="34634-277">The size can be set only as a constant.</span></span> <span data-ttu-id="34634-278">Poniższy kod przedstawia odpowiedniego zarządzanej definicji `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="34634-278">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="34634-279">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="34634-279">See Also</span></span>  
 [<span data-ttu-id="34634-280">Domyślne zachowanie Marshalingu</span><span class="sxs-lookup"><span data-stu-id="34634-280">Default Marshaling Behavior</span></span>](../../../docs/framework/interop/default-marshaling-behavior.md)  
 [<span data-ttu-id="34634-281">Typy Kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="34634-281">Blittable and Non-Blittable Types</span></span>](../../../docs/framework/interop/blittable-and-non-blittable-types.md)  
 [<span data-ttu-id="34634-282">Atrybuty kierunkową</span><span class="sxs-lookup"><span data-stu-id="34634-282">Directional Attributes</span></span>](http://msdn.microsoft.com/en-us/241ac5b5-928e-4969-8f58-1dbc048f9ea2)  
 [<span data-ttu-id="34634-283">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="34634-283">Copying and Pinning</span></span>](../../../docs/framework/interop/copying-and-pinning.md)
