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
ms.openlocfilehash: 1f29420038276739623c534656a94e13080637c6
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64626356"
---
# <a name="default-marshaling-for-arrays"></a><span data-ttu-id="0682f-102">Organizowanie domyślne dotyczące tablic</span><span class="sxs-lookup"><span data-stu-id="0682f-102">Default Marshaling for Arrays</span></span>
<span data-ttu-id="0682f-103">W aplikacji składających się wyłącznie z kodu zarządzanego środowisko uruchomieniowe języka wspólnego przekazuje typy tablic jako we/wy parametrów.</span><span class="sxs-lookup"><span data-stu-id="0682f-103">In an application consisting entirely of managed code, the common language runtime passes array types as In/Out parameters.</span></span> <span data-ttu-id="0682f-104">Z kolei Organizator międzyoperacyjny przekazuje tablicę, tak jak parametry domyślne.</span><span class="sxs-lookup"><span data-stu-id="0682f-104">In contrast, the interop marshaler passes an array as In parameters by default.</span></span>  
  
 <span data-ttu-id="0682f-105">Za pomocą [przypinania optymalizacji](copying-and-pinning.md), tablicy danych kopiowalnych może okazać się działać jako In/Out parametru podczas interakcji z obiektów w tej samej typu apartment.</span><span class="sxs-lookup"><span data-stu-id="0682f-105">With [pinning optimization](copying-and-pinning.md), a blittable array can appear to operate as an In/Out parameter when interacting with objects in the same apartment.</span></span> <span data-ttu-id="0682f-106">Jeśli później wyeksportować kod na bibliotekę typów, używany do generowania serwera proxy między komputerami oraz biblioteki jest używany do organizowania wywołania w apartamentach wywołania można przywrócić na wartość true w zachowaniu parametru.</span><span class="sxs-lookup"><span data-stu-id="0682f-106">However, if you later export the code to a type library used to generate the cross-machine proxy, and that library is used to marshal your calls across apartments, the calls can revert to true In parameter behavior.</span></span>  
  
 <span data-ttu-id="0682f-107">Tablice są skomplikowane ze względu na charakter, a różnice między zarządzanymi i niezarządzanymi macierzami oświadcza informacji od innych typów niekopiowalnych.</span><span class="sxs-lookup"><span data-stu-id="0682f-107">Arrays are complex by nature, and the distinctions between managed and unmanaged arrays warrant more information than other non-blittable types.</span></span>  
  
## <a name="managed-arrays"></a><span data-ttu-id="0682f-108">Zarządzane tablice</span><span class="sxs-lookup"><span data-stu-id="0682f-108">Managed Arrays</span></span>  
 <span data-ttu-id="0682f-109">Zarządzane tablicy, która może się różnić typów; jednak <xref:System.Array?displayProperty=nameWithType> klasy jest klasą bazową wszystkich typów tablicowych.</span><span class="sxs-lookup"><span data-stu-id="0682f-109">Managed array types can vary; however, the <xref:System.Array?displayProperty=nameWithType> class is the base class of all array types.</span></span> <span data-ttu-id="0682f-110">**System.Array** klasa posiada właściwości, określając rangę, długość i dolną i górną granicę, tablica, a także metody uzyskiwania dostępu do, sortowanie, wyszukiwanie, kopiowanie i tworzenie tablic.</span><span class="sxs-lookup"><span data-stu-id="0682f-110">The **System.Array** class has properties for determining the rank, length, and lower and upper bounds of an array, as well as methods for accessing, sorting, searching, copying, and creating arrays.</span></span>  
  
 <span data-ttu-id="0682f-111">Te typy tablic są dynamiczne i nie ma odpowiedniego typu statycznego zdefiniowane w bibliotece klas podstawowych.</span><span class="sxs-lookup"><span data-stu-id="0682f-111">These array types are dynamic and do not have a corresponding static type defined in the base class library.</span></span> <span data-ttu-id="0682f-112">Jest to dobrze jest myśleć o każdej kombinacji typ elementu i rangi jako typ samodzielny tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-112">It is convenient to think of each combination of element type and rank as a distinct type of array.</span></span> <span data-ttu-id="0682f-113">Dlatego Jednowymiarowa tablica liczb całkowitych jest innego typu niż Jednowymiarowa tablica typu double.</span><span class="sxs-lookup"><span data-stu-id="0682f-113">Therefore, a one-dimensional array of integers is of a different type than a one-dimensional array of double types.</span></span> <span data-ttu-id="0682f-114">Podobnie tablicę dwuwymiarową liczb całkowitych różni się od Jednowymiarowa tablica liczb całkowitych.</span><span class="sxs-lookup"><span data-stu-id="0682f-114">Similarly a two-dimensional array of integers is different from a one-dimensional array of integers.</span></span> <span data-ttu-id="0682f-115">Granice tablicy nie są uwzględniane podczas porównywania typów.</span><span class="sxs-lookup"><span data-stu-id="0682f-115">The bounds of the array are not considered when comparing types.</span></span>  
  
 <span data-ttu-id="0682f-116">Jak pokazano w poniższej tabeli, dowolne wystąpienie tablicy zarządzanej musi być typu określonego elementu, rangę i dolną granicę.</span><span class="sxs-lookup"><span data-stu-id="0682f-116">As the following table shows, any instance of a managed array must be of a specific element type, rank, and lower bound.</span></span>  
  
|<span data-ttu-id="0682f-117">Zarządzany typ tablicy</span><span class="sxs-lookup"><span data-stu-id="0682f-117">Managed array type</span></span>|<span data-ttu-id="0682f-118">Typ elementu</span><span class="sxs-lookup"><span data-stu-id="0682f-118">Element type</span></span>|<span data-ttu-id="0682f-119">Ranga</span><span class="sxs-lookup"><span data-stu-id="0682f-119">Rank</span></span>|<span data-ttu-id="0682f-120">Dolna granica</span><span class="sxs-lookup"><span data-stu-id="0682f-120">Lower bound</span></span>|<span data-ttu-id="0682f-121">Notacja podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-121">Signature notation</span></span>|  
|------------------------|------------------|----------|-----------------|------------------------|  
|<span data-ttu-id="0682f-122">**ELEMENT_TYPE_ARRAY**</span><span class="sxs-lookup"><span data-stu-id="0682f-122">**ELEMENT_TYPE_ARRAY**</span></span>|<span data-ttu-id="0682f-123">Określony według typu.</span><span class="sxs-lookup"><span data-stu-id="0682f-123">Specified by type.</span></span>|<span data-ttu-id="0682f-124">Określony według rangi.</span><span class="sxs-lookup"><span data-stu-id="0682f-124">Specified by rank.</span></span>|<span data-ttu-id="0682f-125">Opcjonalnie określone przez granice.</span><span class="sxs-lookup"><span data-stu-id="0682f-125">Optionally specified by bounds.</span></span>|<span data-ttu-id="0682f-126">*Typ* **[** *n*,*m* **]**</span><span class="sxs-lookup"><span data-stu-id="0682f-126">*type* **[** *n*,*m* **]**</span></span>|  
|<span data-ttu-id="0682f-127">**ELEMENT_TYPE_CLASS**</span><span class="sxs-lookup"><span data-stu-id="0682f-127">**ELEMENT_TYPE_CLASS**</span></span>|<span data-ttu-id="0682f-128">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0682f-128">Unknown</span></span>|<span data-ttu-id="0682f-129">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0682f-129">Unknown</span></span>|<span data-ttu-id="0682f-130">Nieznany</span><span class="sxs-lookup"><span data-stu-id="0682f-130">Unknown</span></span>|<span data-ttu-id="0682f-131">**System.Array**</span><span class="sxs-lookup"><span data-stu-id="0682f-131">**System.Array**</span></span>|  
|<span data-ttu-id="0682f-132">**ELEMENT_TYPE_SZARRAY**</span><span class="sxs-lookup"><span data-stu-id="0682f-132">**ELEMENT_TYPE_SZARRAY**</span></span>|<span data-ttu-id="0682f-133">Określony według typu.</span><span class="sxs-lookup"><span data-stu-id="0682f-133">Specified by type.</span></span>|<span data-ttu-id="0682f-134">1</span><span class="sxs-lookup"><span data-stu-id="0682f-134">1</span></span>|<span data-ttu-id="0682f-135">0</span><span class="sxs-lookup"><span data-stu-id="0682f-135">0</span></span>|<span data-ttu-id="0682f-136">*Typ* **[** *n* **]**</span><span class="sxs-lookup"><span data-stu-id="0682f-136">*type* **[** *n* **]**</span></span>|  
  
## <a name="unmanaged-arrays"></a><span data-ttu-id="0682f-137">Tablice niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="0682f-137">Unmanaged Arrays</span></span>  
 <span data-ttu-id="0682f-138">Niezarządzane tablice są tablic bezpiecznych styl modelu COM lub tablice stylu C o długości stałą lub zmienną.</span><span class="sxs-lookup"><span data-stu-id="0682f-138">Unmanaged arrays are either COM-style safe arrays or C-style arrays with fixed or variable length.</span></span> <span data-ttu-id="0682f-139">Tablice bezpieczne są samoopisujące tablic, wykonujących typu, rangę i granice skojarzonych danych.</span><span class="sxs-lookup"><span data-stu-id="0682f-139">Safe arrays are self-describing arrays that carry the type, rank, and bounds of the associated array data.</span></span> <span data-ttu-id="0682f-140">Tablice stylu C są jednowymiarowe tablice o określonym typie ze stałym dolną granicę równą 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-140">C-style arrays are one-dimensional typed arrays with a fixed lower bound of 0.</span></span> <span data-ttu-id="0682f-141">Usługa kierowania ma ograniczoną obsługę oba typy tablic.</span><span class="sxs-lookup"><span data-stu-id="0682f-141">The marshaling service has limited support for both types of arrays.</span></span>  
  
## <a name="passing-array-parameters-to-net-code"></a><span data-ttu-id="0682f-142">Przekazywanie parametrów tablicy do kodu platformy .NET</span><span class="sxs-lookup"><span data-stu-id="0682f-142">Passing Array Parameters to .NET Code</span></span>  
 <span data-ttu-id="0682f-143">Tablice stylu C i tablic bezpiecznych programu mogą być przekazywane do kodu platformy .NET z niezarządzanego kodu jako bezpiecznego tablicy lub tablicy stylu C.</span><span class="sxs-lookup"><span data-stu-id="0682f-143">Both C-style arrays and safe arrays can be passed to .NET code from unmanaged code as either a safe array or a C-style array.</span></span> <span data-ttu-id="0682f-144">W poniższej tabeli przedstawiono wartości typu niezarządzanego i zaimportowanym typem.</span><span class="sxs-lookup"><span data-stu-id="0682f-144">The following table shows the unmanaged type value and the imported type.</span></span>  
  
|<span data-ttu-id="0682f-145">Typ niezarządzany</span><span class="sxs-lookup"><span data-stu-id="0682f-145">Unmanaged type</span></span>|<span data-ttu-id="0682f-146">Typu importowanego</span><span class="sxs-lookup"><span data-stu-id="0682f-146">Imported type</span></span>|  
|--------------------|-------------------|  
|<span data-ttu-id="0682f-147">**SafeArray (** *typu* **)**</span><span class="sxs-lookup"><span data-stu-id="0682f-147">**SafeArray(** *Type* **)**</span></span>|<span data-ttu-id="0682f-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="0682f-148">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="0682f-149">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-149">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="0682f-150">Rozmiar jest znane tylko wtedy, gdy jest podawany jako zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="0682f-150">Size is known only if provided in the managed signature.</span></span> <span data-ttu-id="0682f-151">Bezpieczne tablic, które nie są rangi = 1 lub dolna granica = 0 nie mogą być przekazywane jako **SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0682f-151">Safe arrays that are not rank = 1 or lower bound = 0 cannot be marshaled as **SZARRAY**.</span></span>|  
|<span data-ttu-id="0682f-152">*Typ\*\*\*]*\* </span><span class="sxs-lookup"><span data-stu-id="0682f-152">*Type*  **[]**</span></span>|<span data-ttu-id="0682f-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span><span class="sxs-lookup"><span data-stu-id="0682f-153">**ELEMENT_TYPE_SZARRAY** **\<** *ConvertedType* **>**</span></span><br /><br /> <span data-ttu-id="0682f-154">Ranga = 1, dolna granica = 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-154">Rank = 1, lower bound = 0.</span></span> <span data-ttu-id="0682f-155">Rozmiar jest znane tylko wtedy, gdy jest podawany jako zarządzanego podpisu.</span><span class="sxs-lookup"><span data-stu-id="0682f-155">Size is known only if provided in the managed signature.</span></span>|  
  
### <a name="safe-arrays"></a><span data-ttu-id="0682f-156">Tablic bezpiecznych programu</span><span class="sxs-lookup"><span data-stu-id="0682f-156">Safe Arrays</span></span>  
 <span data-ttu-id="0682f-157">Po zaimportowaniu bezpieczną tablicą z biblioteki typów na zestaw .NET tablica jest konwertowana na tablicę jednowymiarową znanego typu (takie jak **int**).</span><span class="sxs-lookup"><span data-stu-id="0682f-157">When a safe array is imported from a type library to a .NET assembly, the array is converted to a one-dimensional array of a known type (such as **int**).</span></span> <span data-ttu-id="0682f-158">Tych samych zasad konwersji typów, które są stosowane do parametrów dotyczą również elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-158">The same type conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="0682f-159">Na przykład, bezpieczną tablicą o **BSTR** typy staje się zarządzanych tablicę ciągów i bezpieczną tablicą wariantów staje się tablicy obiektów.</span><span class="sxs-lookup"><span data-stu-id="0682f-159">For example, a safe array of **BSTR** types becomes a managed array of strings and a safe array of variants becomes a managed array of objects.</span></span> <span data-ttu-id="0682f-160">**SAFEARRAY** typ elementu jest przechwytywane z biblioteki typów i zapisane w **SAFEARRAY** wartość <xref:System.Runtime.InteropServices.UnmanagedType> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="0682f-160">The **SAFEARRAY** element type is captured from the type library and saved in the **SAFEARRAY** value of the <xref:System.Runtime.InteropServices.UnmanagedType> enumeration.</span></span>  
  
 <span data-ttu-id="0682f-161">Ponieważ nie można ustalić rangi i granice tablicy bezpieczne z biblioteki typów, rangę zakłada, że jest równa 1, a dolna granica zakłada, że jest równa 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-161">Because the rank and bounds of the safe array cannot be determined from the type library, the rank is assumed to equal 1 and the lower bound is assumed to equal 0.</span></span> <span data-ttu-id="0682f-162">Ranga i granice muszą być zdefiniowane w zarządzanego podpisu produkowane przez [Importer biblioteki typów (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span><span class="sxs-lookup"><span data-stu-id="0682f-162">The rank and bounds must be defined in the managed signature produced by the [Type Library Importer (Tlbimp.exe)](../tools/tlbimp-exe-type-library-importer.md).</span></span> <span data-ttu-id="0682f-163">Jeśli różni się rangę przekazywany do metody w czasie wykonywania, <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="0682f-163">If the rank passed to the method at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayRankMismatchException> is thrown.</span></span> <span data-ttu-id="0682f-164">Jeśli typ tablicy przekazany w czasie wykonywania jest inny, <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> zgłaszany.</span><span class="sxs-lookup"><span data-stu-id="0682f-164">If the type of the array passed at run time differs, a <xref:System.Runtime.InteropServices.SafeArrayTypeMismatchException> is thrown.</span></span> <span data-ttu-id="0682f-165">Poniższy przykład pokazuje tablic bezpiecznych w kodzie zarządzanym i niezarządzanym.</span><span class="sxs-lookup"><span data-stu-id="0682f-165">The following example shows safe arrays in managed and unmanaged code.</span></span>  
  
 <span data-ttu-id="0682f-166">**Niezarządzane podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-166">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1([in] SAFEARRAY( int ) ar);  
HRESULT New2([in] SAFEARRAY( DATE ) ar);  
HRESULT New3([in, out] SAFEARRAY( BSTR ) *ar);  
```  
  
 <span data-ttu-id="0682f-167">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-167">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0682f-168">Wielowymiarowym lub różną od zera powiązane z tablic bezpiecznych, może być organizowany wywołanie kodu zarządzanego, jeśli podpis metody generowane przez Tlbimp.exe jest modyfikowany, aby wskazać typ elementu **ELEMENT_TYPE_ARRAY** zamiast **ELEMENT_ TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0682f-168">Multidimensional, or nonzero-bound safe arrays, can be marshaled into managed code if the method signature produced by Tlbimp.exe is modified to indicate an element type of **ELEMENT_TYPE_ARRAY** instead of **ELEMENT_TYPE_SZARRAY**.</span></span> <span data-ttu-id="0682f-169">Alternatywnie, można użyć **/sysarray** Przełącz przy użyciu Tlbimp.exe do importowania wszystkich tablic jako <xref:System.Array?displayProperty=nameWithType> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0682f-169">Alternatively, you can use the **/sysarray** switch with Tlbimp.exe to import all arrays as <xref:System.Array?displayProperty=nameWithType> objects.</span></span> <span data-ttu-id="0682f-170">W przypadkach, w którym tablicy przekazywana jest znany jako wielowymiarowe można edytować utworzony kod intermediate language (MSIL) firmy Microsoft przez Tlbimp.exe i skompiluj go ponownie.</span><span class="sxs-lookup"><span data-stu-id="0682f-170">In cases where the array being passed is known to be multidimensional, you can edit the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompile it.</span></span> <span data-ttu-id="0682f-171">Aby uzyskać szczegółowe informacje dotyczące sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0682f-171">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span>  
  
### <a name="c-style-arrays"></a><span data-ttu-id="0682f-172">Tablice stylu C</span><span class="sxs-lookup"><span data-stu-id="0682f-172">C-Style Arrays</span></span>  
 <span data-ttu-id="0682f-173">Po zaimportowaniu tablicy stylu C z biblioteki typów na zestaw .NET tablica jest konwertowana na **ELEMENT_TYPE_SZARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0682f-173">When a C-style array is imported from a type library to a .NET assembly, the array is converted to **ELEMENT_TYPE_SZARRAY**.</span></span>  
  
 <span data-ttu-id="0682f-174">Typ elementu tablicy jest określana na podstawie biblioteki typów i zachowywane podczas importowania.</span><span class="sxs-lookup"><span data-stu-id="0682f-174">The array element type is determined from the type library and preserved during the import.</span></span> <span data-ttu-id="0682f-175">Te same reguły konwersji, które są stosowane do parametrów dotyczą również elementy tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-175">The same conversion rules that apply to parameters also apply to array elements.</span></span> <span data-ttu-id="0682f-176">Na przykład tablica **LPStr** typy staje się tablica **ciąg** typów.</span><span class="sxs-lookup"><span data-stu-id="0682f-176">For example, an array of **LPStr** types becomes an array of **String** types.</span></span> <span data-ttu-id="0682f-177">Tlbimp.exe przechwytuje typ elementu tablicy i stosuje <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu do parametru.</span><span class="sxs-lookup"><span data-stu-id="0682f-177">Tlbimp.exe captures the array element type and applies the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute to the parameter.</span></span>  
  
 <span data-ttu-id="0682f-178">Ranga tablicy, przyjmowana jest wartość 1.</span><span class="sxs-lookup"><span data-stu-id="0682f-178">The array rank is assumed to equal 1.</span></span> <span data-ttu-id="0682f-179">Jeśli pozycja jest większa niż 1, tablica jest organizowana jako Jednowymiarowa tablica, w kolejności kolumn.</span><span class="sxs-lookup"><span data-stu-id="0682f-179">If the rank is greater than 1, the array is marshaled as a one-dimensional array in column-major order.</span></span> <span data-ttu-id="0682f-180">Dolna granica jest zawsze równa 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-180">The lower bound always equals 0.</span></span>  
  
 <span data-ttu-id="0682f-181">Biblioteki typów mogą zawierać tablic o długości stałą lub zmienną.</span><span class="sxs-lookup"><span data-stu-id="0682f-181">Type libraries can contain arrays of fixed or variable length.</span></span> <span data-ttu-id="0682f-182">Tlbimp.exe można importować tylko o stałej długości tablic z bibliotek typów, ponieważ biblioteki typów brakuje informacji potrzebnych do organizowania tablice o zmiennej długości.</span><span class="sxs-lookup"><span data-stu-id="0682f-182">Tlbimp.exe can import only fixed-length arrays from type libraries because type libraries lack the information needed to marshal variable-length arrays.</span></span> <span data-ttu-id="0682f-183">W przypadku tablic o stałej długości, rozmiar zaimportowano z biblioteki typów i przechwycone w **MarshalAsAttribute** który został zastosowany do parametru.</span><span class="sxs-lookup"><span data-stu-id="0682f-183">With fixed-length arrays, the size is imported from the type library and captured in the **MarshalAsAttribute** that is applied to the parameter.</span></span>  
  
 <span data-ttu-id="0682f-184">Trzeba ręcznie zdefiniować biblioteki typów zawierające tablice o zmiennej długości, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="0682f-184">You must manually define type libraries containing variable-length arrays, as shown in the following example.</span></span>  
  
 <span data-ttu-id="0682f-185">**Niezarządzane podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-185">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[10]);  
HRESULT New2(double ar[10][20]);  
HRESULT New3(LPWStr ar[10]);  
```  
  
 <span data-ttu-id="0682f-186">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-186">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0682f-187">Chociaż można stosować **size_is** lub **length_is —** atrybuty do tablicy w źródle języka definicji interfejsu (IDL) w celu przekazania rozmiaru na kliencie Microsoft Interface Definition Language (MIDL) Kompilator nie propaguje tych informacji do biblioteki typów.</span><span class="sxs-lookup"><span data-stu-id="0682f-187">Although you can apply the **size_is** or **length_is** attributes to an array in Interface Definition Language (IDL) source to convey the size to a client, the Microsoft Interface Definition Language (MIDL) compiler does not propagate that information to the type library.</span></span> <span data-ttu-id="0682f-188">Nie wiedząc o tym rozmiar, współdziałanie marshaling usługi nie można zorganizować elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-188">Without knowing the size, the interop marshaling service cannot marshal the array elements.</span></span> <span data-ttu-id="0682f-189">W związku z tym tablice o zmiennej długości są importowane jako argumenty odwołania.</span><span class="sxs-lookup"><span data-stu-id="0682f-189">Consequently, variable-length arrays are imported as reference arguments.</span></span> <span data-ttu-id="0682f-190">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-190">For example:</span></span>  
  
 <span data-ttu-id="0682f-191">**Niezarządzane podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-191">**Unmanaged signature**</span></span>  
  
```  
HRESULT New1(int ar[]);  
HRESULT New2(int ArSize, [size_is(ArSize)] double ar[]);  
HRESULT New3(int ElemCnt, [length_is(ElemCnt)] LPStr ar[]);  
```  
  
 <span data-ttu-id="0682f-192">**Zarządzanego podpisu**</span><span class="sxs-lookup"><span data-stu-id="0682f-192">**Managed signature**</span></span>  
  
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
  
 <span data-ttu-id="0682f-193">Możesz zapewnić Organizator rozmiar tablicy generowany kod intermediate language (MSIL) firmy Microsoft przez Tlbimp.exe do edycji, a następnie ponownego kompilowania.</span><span class="sxs-lookup"><span data-stu-id="0682f-193">You can provide the marshaler with the array size by editing the Microsoft intermediate language (MSIL) code produced by Tlbimp.exe and then recompiling it.</span></span> <span data-ttu-id="0682f-194">Aby uzyskać szczegółowe informacje dotyczące sposobu modyfikowania kodu MSIL, zobacz [Dostosowywanie wywoływanych otok środowiska uruchomieniowego](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="0682f-194">For details about how to modify MSIL code, see [Customizing Runtime Callable Wrappers](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/e753eftz(v=vs.100)).</span></span> <span data-ttu-id="0682f-195">Wskaż liczbę elementów w tablicy, zastosuj <xref:System.Runtime.InteropServices.MarshalAsAttribute> typ parametru tablicy definicji metody zarządzanego w jednym z następujących sposobów:</span><span class="sxs-lookup"><span data-stu-id="0682f-195">To indicate the number of elements in the array, apply the <xref:System.Runtime.InteropServices.MarshalAsAttribute> type to the array parameter of the managed method definition in one of the following ways:</span></span>  
  
- <span data-ttu-id="0682f-196">Określ inny parametr, który zawiera liczbę elementów w tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-196">Identify another parameter that contains the number of elements in the array.</span></span> <span data-ttu-id="0682f-197">Parametry są identyfikowane według położenia, rozpoczynając od pierwszego parametru jako numer 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-197">The parameters are identified by position, starting with the first parameter as number 0.</span></span>     
  
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
  
- <span data-ttu-id="0682f-198">Zdefiniować rozmiar tablicy jako stała.</span><span class="sxs-lookup"><span data-stu-id="0682f-198">Define the size of the array as a constant.</span></span> <span data-ttu-id="0682f-199">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-199">For example:</span></span>  
  
    ```vb  
    Sub [New](\<MarshalAs(UnmanagedType.LPArray, SizeConst:=128)> _  
       ar() As Integer)  
    ```  
  
    ```csharp  
    void New(  
       [MarshalAs(UnmanagedType.LPArray, SizeConst=128)] int[] ar );  
    ```  
  
 <span data-ttu-id="0682f-200">Podczas przekazywania tablic z niezarządzanego kodu do kodu zarządzanego, organizator sprawdza **MarshalAsAttribute** skojarzone z parametru, aby określić rozmiar tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-200">When marshaling arrays from unmanaged code to managed code, the marshaler checks the **MarshalAsAttribute** associated with the parameter to determine the array size.</span></span> <span data-ttu-id="0682f-201">Jeśli rozmiar tablicy nie jest określona, tylko jeden element jest organizowany.</span><span class="sxs-lookup"><span data-stu-id="0682f-201">If the array size is not specified, only one element is marshaled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0682f-202">**MarshalAsAttribute** nie wpływa na przekazywanie zarządzane macierze do kodu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0682f-202">The **MarshalAsAttribute** has no effect on marshaling managed arrays to unmanaged code.</span></span> <span data-ttu-id="0682f-203">W tym kierunku rozmiar tablicy jest określana przez badanie.</span><span class="sxs-lookup"><span data-stu-id="0682f-203">In that direction, the array size is determined by examination.</span></span> <span data-ttu-id="0682f-204">Nie ma możliwości marshalingu podzbiór tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0682f-204">There is no way to marshal a subset of a managed array.</span></span>  
  
 <span data-ttu-id="0682f-205">Organizator międzyoperacyjny używa **CoTaskMemAlloc** i **CoTaskMemFree** metody przydzielania i pobrać pamięci.</span><span class="sxs-lookup"><span data-stu-id="0682f-205">The interop marshaler uses the **CoTaskMemAlloc** and **CoTaskMemFree** methods to allocate and retrieve memory.</span></span> <span data-ttu-id="0682f-206">Alokacja pamięci wykonywane przez kod niezarządzany, należy również użyć tych metod.</span><span class="sxs-lookup"><span data-stu-id="0682f-206">Memory allocation performed by unmanaged code must also use these methods.</span></span>  
  
## <a name="passing-arrays-to-com"></a><span data-ttu-id="0682f-207">Przekazywanie tablic modelowi COM</span><span class="sxs-lookup"><span data-stu-id="0682f-207">Passing Arrays to COM</span></span>  
 <span data-ttu-id="0682f-208">Wszystkie typy tablic zarządzanych mogą być przekazywane do kodu niezarządzanego z kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="0682f-208">All managed array types can be passed to unmanaged code from managed code.</span></span> <span data-ttu-id="0682f-209">W zależności od typu zarządzanego i atrybuty stosowane do niego tablicy może zostać oceniony jako bezpiecznej tablicy lub tablicy stylu C, jak pokazano w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="0682f-209">Depending on the managed type and the attributes applied to it, the array can be accessed as a safe array or a C-style array, as shown in the following table.</span></span>  
  
|<span data-ttu-id="0682f-210">Zarządzany typ tablicy</span><span class="sxs-lookup"><span data-stu-id="0682f-210">Managed array type</span></span>|<span data-ttu-id="0682f-211">Wyeksportowany jako</span><span class="sxs-lookup"><span data-stu-id="0682f-211">Exported as</span></span>|  
|------------------------|-----------------|  
|<span data-ttu-id="0682f-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span><span class="sxs-lookup"><span data-stu-id="0682f-212">**ELEMENT_TYPE_SZARRAY** **\<** *type* **>**</span></span>|<span data-ttu-id="0682f-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="0682f-213"><xref:System.Runtime.InteropServices.UnmanagedType> **.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0682f-214">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="0682f-214">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="0682f-215">Typ jest dostarczany w podpisie.</span><span class="sxs-lookup"><span data-stu-id="0682f-215">Type is provided in the signature.</span></span> <span data-ttu-id="0682f-216">Ranga ma zawsze numer 1, dolna granica jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-216">Rank is always 1, lower bound is always 0.</span></span> <span data-ttu-id="0682f-217">Rozmiar zawsze jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0682f-217">Size is always known at run time.</span></span>|  
|<span data-ttu-id="0682f-218">**ELEMENT_TYPE_ARRAY** **\<** *typu* **>** **\<** *ranga* **>**[**\<** *granice* **>**]</span><span class="sxs-lookup"><span data-stu-id="0682f-218">**ELEMENT_TYPE_ARRAY** **\<** *type* **>** **\<** *rank* **>**[**\<** *bounds* **>**]</span></span>|<span data-ttu-id="0682f-219">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="0682f-219">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0682f-220">**UnmanagedType.LPArray**</span><span class="sxs-lookup"><span data-stu-id="0682f-220">**UnmanagedType.LPArray**</span></span><br /><br /> <span data-ttu-id="0682f-221">Granice rangę, typ, znajdują się w podpisie.</span><span class="sxs-lookup"><span data-stu-id="0682f-221">Type, rank, bounds are provided in the signature.</span></span> <span data-ttu-id="0682f-222">Rozmiar zawsze jest znany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0682f-222">Size is always known at run time.</span></span>|  
|<span data-ttu-id="0682f-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span><span class="sxs-lookup"><span data-stu-id="0682f-223">**ELEMENT_TYPE_CLASS** **\<**<xref:System.Array?displayProperty=nameWithType>**>**</span></span>|<span data-ttu-id="0682f-224">**UT_Interface**</span><span class="sxs-lookup"><span data-stu-id="0682f-224">**UT_Interface**</span></span><br /><br /> <span data-ttu-id="0682f-225">**UnmanagedType.SafeArray(** *type* **)**</span><span class="sxs-lookup"><span data-stu-id="0682f-225">**UnmanagedType.SafeArray(** *type* **)**</span></span><br /><br /> <span data-ttu-id="0682f-226">Typ, rangę, granice i rozmiar zawsze są znane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="0682f-226">Type, rank, bounds, and size are always known at run time.</span></span>|  
  
 <span data-ttu-id="0682f-227">Brak ograniczeń w automatyzacji OLE odnoszących się do tablic struktur, które zawierają LPSTR lub LPWSTR.</span><span class="sxs-lookup"><span data-stu-id="0682f-227">There is a limitation in OLE Automation relating to arrays of structures that contain LPSTR or LPWSTR.</span></span>  <span data-ttu-id="0682f-228">W związku z tym **ciąg** pola muszą być przekazywane jako **UnmanagedType.BSTR**.</span><span class="sxs-lookup"><span data-stu-id="0682f-228">Therefore, **String** fields have to be marshaled as **UnmanagedType.BSTR**.</span></span> <span data-ttu-id="0682f-229">W przeciwnym razie zostanie zgłoszony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="0682f-229">Otherwise, an exception will be thrown.</span></span>  
  
### <a name="elementtypeszarray"></a><span data-ttu-id="0682f-230">ELEMENT_TYPE_SZARRAY</span><span class="sxs-lookup"><span data-stu-id="0682f-230">ELEMENT_TYPE_SZARRAY</span></span>  
 <span data-ttu-id="0682f-231">Gdy metoda zawiera **ELEMENT_TYPE_SZARRAY** parametru (jednowymiarową) są eksportowane z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="0682f-231">When a method containing an **ELEMENT_TYPE_SZARRAY** parameter (one-dimensional array) is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="0682f-232">Zastosuj te same reguły konwersji do typów elementów tablicy.</span><span class="sxs-lookup"><span data-stu-id="0682f-232">The same conversion rules apply to the array element types.</span></span> <span data-ttu-id="0682f-233">Zawartość tablicy zarządzanej są automatycznie kopiowane z pamięci zarządzanej do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0682f-233">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="0682f-234">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-234">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-235">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-235">Managed signature</span></span>  
  
```vb  
Sub [New](ar() As Long)  
Sub [New](ar() As String)  
```  
  
```csharp  
void New(long[] ar );  
void New(String[] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0682f-236">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-236">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="0682f-237">Ranga tablic bezpiecznych ma zawsze numer 1 i dolna granica jest zawsze 0.</span><span class="sxs-lookup"><span data-stu-id="0682f-237">The rank of the safe arrays is always 1 and the lower bound is always 0.</span></span> <span data-ttu-id="0682f-238">Rozmiar jest określany w czasie wykonywania przez rozmiar tablicy zarządzanej przekazywana.</span><span class="sxs-lookup"><span data-stu-id="0682f-238">The size is determined at run time by the size of the managed array being passed.</span></span>  
  
 <span data-ttu-id="0682f-239">Tablica również może być organizowany jako tablicy stylu C za pomocą <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0682f-239">The array can also be marshaled as a C-style array by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0682f-240">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-240">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-241">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-241">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0682f-242">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-242">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(BSTR ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="0682f-243">Mimo że organizator ma długość potrzebnych do organizowania tablicy, długość tablicy zwykle jest przekazywany jako osobne argument przekazuję długość obiekt wywoływany.</span><span class="sxs-lookup"><span data-stu-id="0682f-243">Although the marshaler has the length information needed to marshal the array, the array length is usually passed as a separate argument to convey the length to the callee.</span></span>  
  
### <a name="elementtypearray"></a><span data-ttu-id="0682f-244">ELEMENT_TYPE_ARRAY</span><span class="sxs-lookup"><span data-stu-id="0682f-244">ELEMENT_TYPE_ARRAY</span></span>  
 <span data-ttu-id="0682f-245">Gdy metoda zawiera **ELEMENT_TYPE_ARRAY** parametru została wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **SAFEARRAY** danego typu.</span><span class="sxs-lookup"><span data-stu-id="0682f-245">When a method containing an **ELEMENT_TYPE_ARRAY** parameter is exported from a .NET assembly to a type library, the array parameter is converted to a **SAFEARRAY** of a given type.</span></span> <span data-ttu-id="0682f-246">Zawartość tablicy zarządzanej są automatycznie kopiowane z pamięci zarządzanej do **SAFEARRAY**.</span><span class="sxs-lookup"><span data-stu-id="0682f-246">The contents of the managed array are automatically copied from managed memory into the **SAFEARRAY**.</span></span> <span data-ttu-id="0682f-247">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-247">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-248">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-248">Managed signature</span></span>  
  
```vb  
Sub [New](ar(,) As Long)  
Sub [New](ar(,) As String)  
```  
  
```csharp  
void New( long [,] ar );  
void New( String [,] ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0682f-249">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-249">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] SAFEARRAY( long ) ar);   
HRESULT New([in] SAFEARRAY( BSTR ) ar);  
```  
  
 <span data-ttu-id="0682f-250">Rangę, rozmiar i granice tablic bezpiecznych są określane w czasie wykonywania przez właściwości tablicy zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="0682f-250">The rank, size, and bounds of the safe arrays are determined at run time by the characteristics of the managed array.</span></span>  
  
 <span data-ttu-id="0682f-251">Tablicy również może być organizowany jako tablicy stylu C, stosując <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0682f-251">The array can also be marshaled as a C-style array by applying the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0682f-252">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-252">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-253">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-253">Managed signature</span></span>  
  
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
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0682f-254">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-254">Unmanaged signature</span></span>  
  
```  
HRESULT New(long ar[]);   
HRESULT New(LPStr ar[]);  
```  
  
 <span data-ttu-id="0682f-255">Tablice zagnieżdżone nie mogą być przekazywane.</span><span class="sxs-lookup"><span data-stu-id="0682f-255">Nested arrays cannot be marshaled.</span></span> <span data-ttu-id="0682f-256">Na przykład, następujący podpis generuje błąd podczas eksportowania z [Eksporter biblioteki typów (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span><span class="sxs-lookup"><span data-stu-id="0682f-256">For example, the following signature generates an error when exported with the [Type Library Exporter (Tlbexp.exe)](../tools/tlbexp-exe-type-library-exporter.md).</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-257">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-257">Managed signature</span></span>  
  
```vb  
Sub [New](ar()()() As Long)  
```  
  
```csharp  
void New(long [][][] ar );  
```  
  
### <a name="elementtypeclass-systemarray"></a><span data-ttu-id="0682f-258">ELEMENT_TYPE_CLASS \<System.Array></span><span class="sxs-lookup"><span data-stu-id="0682f-258">ELEMENT_TYPE_CLASS \<System.Array></span></span>  
 <span data-ttu-id="0682f-259">Gdy metoda zawiera <xref:System.Array?displayProperty=nameWithType> parametru została wyeksportowana z zestawu .NET do biblioteki typów, parametr tablicy jest konwertowany na **_Array** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0682f-259">When a method containing a <xref:System.Array?displayProperty=nameWithType> parameter is exported from a .NET assembly to a type library, the array parameter is converted to an **_Array** interface.</span></span> <span data-ttu-id="0682f-260">Zawartość tablicy zarządzanej jest dostępna tylko za pośrednictwem metody i właściwości **_Array** interfejsu.</span><span class="sxs-lookup"><span data-stu-id="0682f-260">The contents of the managed array are accessible only through the methods and properties of the **_Array** interface.</span></span> <span data-ttu-id="0682f-261">**System.Array** również może być organizowany jako **SAFEARRAY** przy użyciu <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu.</span><span class="sxs-lookup"><span data-stu-id="0682f-261">**System.Array** can also be marshaled as a **SAFEARRAY** by using the <xref:System.Runtime.InteropServices.MarshalAsAttribute> attribute.</span></span> <span data-ttu-id="0682f-262">Podczas przekazywania jako bezpieczną tablicą, elementy tablicy są organizowana jako wariantów.</span><span class="sxs-lookup"><span data-stu-id="0682f-262">When marshaled as a safe array, the array elements are marshaled as variants.</span></span> <span data-ttu-id="0682f-263">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0682f-263">For example:</span></span>  
  
#### <a name="managed-signature"></a><span data-ttu-id="0682f-264">Zarządzanego podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-264">Managed signature</span></span>  
  
```vb  
Sub New1( ar As System.Array )  
Sub New2( <MarshalAs(UnmanagedType.Safe array)> ar As System.Array )  
```  
  
```csharp  
void New1( System.Array ar );  
void New2( [MarshalAs(UnmanagedType.Safe array)] System.Array ar );  
```  
  
#### <a name="unmanaged-signature"></a><span data-ttu-id="0682f-265">Niezarządzane podpisu</span><span class="sxs-lookup"><span data-stu-id="0682f-265">Unmanaged signature</span></span>  
  
```  
HRESULT New([in] _Array *ar);   
HRESULT New([in] SAFEARRAY(VARIANT) ar);  
```  
  
### <a name="arrays-within-structures"></a><span data-ttu-id="0682f-266">Tablice w ramach struktury</span><span class="sxs-lookup"><span data-stu-id="0682f-266">Arrays within Structures</span></span>  
 <span data-ttu-id="0682f-267">Niezarządzane struktury mogą zawierać osadzonych tablic.</span><span class="sxs-lookup"><span data-stu-id="0682f-267">Unmanaged structures can contain embedded arrays.</span></span> <span data-ttu-id="0682f-268">Domyślnie te pola osadzoną tablicę są przekazywane jako obiektu SAFEARRAY.</span><span class="sxs-lookup"><span data-stu-id="0682f-268">By default, these embedded array fields are marshaled as a SAFEARRAY.</span></span> <span data-ttu-id="0682f-269">W poniższym przykładzie `s1` jest osadzoną tablicę, która została przydzielona bezpośrednio w samej strukturze.</span><span class="sxs-lookup"><span data-stu-id="0682f-269">In the following example, `s1` is an embedded array that is allocated directly within the structure itself.</span></span>  
  
#### <a name="unmanaged-representation"></a><span data-ttu-id="0682f-270">Reprezentacji niezarządzanej</span><span class="sxs-lookup"><span data-stu-id="0682f-270">Unmanaged representation</span></span>  
  
```  
struct MyStruct {  
    short s1[128];  
}  
```  
  
 <span data-ttu-id="0682f-271">Tablice mogą być organizowane poza jako <xref:System.Runtime.InteropServices.UnmanagedType>, musisz ustawić <xref:System.Runtime.InteropServices.MarshalAsAttribute> pola.</span><span class="sxs-lookup"><span data-stu-id="0682f-271">Arrays can be marshaled as <xref:System.Runtime.InteropServices.UnmanagedType>, which requires you to set the <xref:System.Runtime.InteropServices.MarshalAsAttribute> field.</span></span> <span data-ttu-id="0682f-272">Rozmiar można ustawić tylko jako stała.</span><span class="sxs-lookup"><span data-stu-id="0682f-272">The size can be set only as a constant.</span></span> <span data-ttu-id="0682f-273">Poniższy kod przedstawia definicję odpowiedniego zarządzanego `MyStruct`.</span><span class="sxs-lookup"><span data-stu-id="0682f-273">The following code shows the corresponding managed definition of `MyStruct`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0682f-274">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0682f-274">See also</span></span>

- [<span data-ttu-id="0682f-275">Domyślne zachowanie marshalingu</span><span class="sxs-lookup"><span data-stu-id="0682f-275">Default Marshaling Behavior</span></span>](default-marshaling-behavior.md)
- [<span data-ttu-id="0682f-276">Typy kopiowalne i niekopiowalne</span><span class="sxs-lookup"><span data-stu-id="0682f-276">Blittable and Non-Blittable Types</span></span>](blittable-and-non-blittable-types.md)
- <span data-ttu-id="0682f-277">[Atrybuty kierunkowe](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="0682f-277">[Directional Attributes](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/77e6taeh(v=vs.100))</span></span>
- [<span data-ttu-id="0682f-278">Kopiowanie i przypinanie</span><span class="sxs-lookup"><span data-stu-id="0682f-278">Copying and Pinning</span></span>](copying-and-pinning.md)
