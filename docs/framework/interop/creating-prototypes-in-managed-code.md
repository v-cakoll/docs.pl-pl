---
title: Tworzenie prototypów w kodzie zarządzanym
ms.date: 03/30/2017
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- prototypes in managed code
- COM interop, DLL functions
- unmanaged functions
- platform invoke, creating prototypes
- COM interop, platform invoke
- interoperation with unmanaged code, DLL functions
- interoperation with unmanaged code, platform invoke
- platform invoke, object fields
- DLL functions
- object fields in platform invoke
ms.assetid: ecdcf25d-cae3-4f07-a2b6-8397ac6dc42d
caps.latest.revision: 22
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: c59a05c5f6abfa30a71ccf7608f8a84738f99c3a
ms.sourcegitcommit: 9a4fe1a1c37b26532654b4bbe22d702237950009
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2018
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="973c7-102">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="973c7-102">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="973c7-103">Ten temat zawiera opis sposobu dostępu z funkcjami niezarządzanymi i wprowadzono kilka pól atrybutów, które adnotacji definicji metody w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="973c7-103">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="973c7-104">Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="973c7-104">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="973c7-105">Przed uzyskaniem dostępu niezarządzanych funkcji DLL z kodu zarządzanego, musisz znać nazwę funkcji i nazwy biblioteki DLL, który eksportuje je.</span><span class="sxs-lookup"><span data-stu-id="973c7-105">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="973c7-106">Dzięki tym informacjom można rozpocząć zapisu zarządzanej definicji niezarządzanej funkcji, która jest zaimplementowana w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="973c7-106">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="973c7-107">Ponadto można dostosować sposób wywołania tej platformy tworzy funkcję i marshals danych do i z funkcji.</span><span class="sxs-lookup"><span data-stu-id="973c7-107">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="973c7-108">Funkcje interfejsu API Win32, które przydzielić ciągu umożliwiają wolne ciąg przy użyciu metody, takie jak `LocalFree`.</span><span class="sxs-lookup"><span data-stu-id="973c7-108">Win32 API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="973c7-109">Wywołanie platformy obsługuje tych parametrów w inny sposób.</span><span class="sxs-lookup"><span data-stu-id="973c7-109">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="973c7-110">Dla platformy wywołania wywołania, określ parametr `IntPtr` wpisz zamiast `String` typu.</span><span class="sxs-lookup"><span data-stu-id="973c7-110">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="973c7-111">Użyj metody, które są udostępniane przez <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> klasę, aby przekonwertować na ciąg typu ręcznie i zwolnij go ręcznie.</span><span class="sxs-lookup"><span data-stu-id="973c7-111">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="973c7-112">Podstawy deklaracji</span><span class="sxs-lookup"><span data-stu-id="973c7-112">Declaration Basics</span></span>  
 <span data-ttu-id="973c7-113">Definicje zarządzanych do niezarządzanych funkcji są zależne od języka, jak to pokazano w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="973c7-113">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="973c7-114">Aby uzyskać bardziej szczegółowy przykłady kodu, zobacz [przykłady wywołania platformy](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="973c7-114">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 <span data-ttu-id="973c7-115">Aby zastosować <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, lub <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> pól do [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] deklaracji, należy użyć <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu zamiast `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="973c7-115">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> fields to a [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
   <DllImport ("user32.dll", CharSet := CharSet.Auto)> _  
   Public Shared Function MessageBox (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
   End Function  
End Class  
```  
  
```csharp  
using System.Runtime.InteropServices;  
[DllImport("user32.dll")]  
    public static extern IntPtr MessageBox(int hWnd, String text,   
                                       String caption, uint type);  
```  
  
```cpp  
using namespace System::Runtime::InteropServices;  
[DllImport("user32.dll")]  
    extern "C" IntPtr MessageBox(int hWnd, String* pText,  
    String* pCaption unsigned int uType);  
```  
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="973c7-116">Dostosowywanie definicji</span><span class="sxs-lookup"><span data-stu-id="973c7-116">Adjusting the Definition</span></span>  
 <span data-ttu-id="973c7-117">Czy zostaną ustawione jawnie lub nie, atrybutu pola są w miejscu pracy Definiowanie zachowania kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="973c7-117">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="973c7-118">Wywołanie platformy działa zgodnie z wartościami domyślnymi, ustawiać różne pola, które istnieją jak metadanych w zestawie.</span><span class="sxs-lookup"><span data-stu-id="973c7-118">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="973c7-119">To zachowanie domyślne można zmienić, dopasowując wartości co najmniej jedno pole.</span><span class="sxs-lookup"><span data-stu-id="973c7-119">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="973c7-120">W wielu przypadkach można użyć <xref:System.Runtime.InteropServices.DllImportAttribute> można ustawić wartości.</span><span class="sxs-lookup"><span data-stu-id="973c7-120">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="973c7-121">W poniższej tabeli wymieniono pełny zestaw atrybut, który pola, które odnoszą się do platformy wywołaniu.</span><span class="sxs-lookup"><span data-stu-id="973c7-121">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="973c7-122">Dla każdego pola w tabeli przedstawiono wartości domyślnej i łącze do informacji na temat korzystania z tych pól do definiowania niezarządzanych funkcji DLL.</span><span class="sxs-lookup"><span data-stu-id="973c7-122">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="973c7-123">Pole</span><span class="sxs-lookup"><span data-stu-id="973c7-123">Field</span></span>|<span data-ttu-id="973c7-124">Opis</span><span class="sxs-lookup"><span data-stu-id="973c7-124">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="973c7-125">Włącza lub wyłącza mapowanie najlepszego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="973c7-125">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="973c7-126">Określa konwencję wywołania do użycia w przekazywanie argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="973c7-126">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="973c7-127">Wartość domyślna to `WinAPI`, które odpowiada `__stdcall` na platformach opartych na Intel 32-bitowych.</span><span class="sxs-lookup"><span data-stu-id="973c7-127">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="973c7-128">Przekręcona nazwa kontrolki i sposób, w jaki argumenty ciągu powinny być przekazywane do funkcji.</span><span class="sxs-lookup"><span data-stu-id="973c7-128">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="973c7-129">Wartość domyślna to `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="973c7-129">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="973c7-130">Określa punkt wejścia biblioteki DLL do wywołania.</span><span class="sxs-lookup"><span data-stu-id="973c7-130">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="973c7-131">Określa, czy punkt wejścia powinien być modyfikowany odpowiadać zestaw znaków.</span><span class="sxs-lookup"><span data-stu-id="973c7-131">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="973c7-132">Wartość domyślna zależy od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="973c7-132">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="973c7-133">Określa, czy transformacji podpis metody zarządzane do niezarządzanego podpisu, która zwraca HRESULT i ma dodatkowe [out, retval] argument dla wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="973c7-133">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="973c7-134">Wartość domyślna to `true` (podpis nie powinien zostać przekształcone).</span><span class="sxs-lookup"><span data-stu-id="973c7-134">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="973c7-135">Obiekt wywołujący, aby użyć umożliwia `Marshal.GetLastWin32Error` funkcja interfejsu API w celu ustalenia, czy wystąpił błąd podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="973c7-135">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="973c7-136">W języku Visual Basic, wartość domyślna to `true`; w języku C# i C++, wartość domyślna to `false`.</span><span class="sxs-lookup"><span data-stu-id="973c7-136">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="973c7-137">Formanty Zgłaszanie wyjątku na zmapować znak Unicode, który jest konwertowany na ANSI "?" znaków.</span><span class="sxs-lookup"><span data-stu-id="973c7-137">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="973c7-138">Aby uzyskać szczegółowe informacje, zobacz <xref:System.Runtime.InteropServices.DllImportAttribute>.</span><span class="sxs-lookup"><span data-stu-id="973c7-138">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="973c7-139">Zagadnienia dotyczące zabezpieczeń wywołanie platformy</span><span class="sxs-lookup"><span data-stu-id="973c7-139">Platform invoke security considerations</span></span>  
 <span data-ttu-id="973c7-140">`Assert`, `Deny`, I `PermitOnly` członkami <xref:System.Security.Permissions.SecurityAction> wyliczenia są określane jako *Modyfikatory przeszukiwania stosu*.</span><span class="sxs-lookup"><span data-stu-id="973c7-140">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="973c7-141">Elementy te są ignorowane, jeśli są używane jako deklaratywne atrybuty na platformie wywołania deklaracje i oświadczenia języka definicji interfejsu COM (IDL).</span><span class="sxs-lookup"><span data-stu-id="973c7-141">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="973c7-142">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="973c7-142">Platform Invoke Examples</span></span>  
 <span data-ttu-id="973c7-143">Wywołanie platformy próbek w tej sekcji przedstawiający zastosowanie `RegistryPermission` atrybutu z modyfikatorami przeszukiwania stosu.</span><span class="sxs-lookup"><span data-stu-id="973c7-143">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="973c7-144">W poniższym przykładzie kodu <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, i `PermitOnly` Modyfikatory są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="973c7-144">In the following code example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionAssert();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="973c7-145">Jednak `Demand` modyfikator w poniższym przykładzie jest akceptowany.</span><span class="sxs-lookup"><span data-stu-id="973c7-145">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="973c7-146"><xref:System.Security.Permissions.SecurityAction> Modyfikatory działają prawidłowo, jeśli zostały one umieszczone na klasę, która zawiera (zawija) platformy wywołaniem.</span><span class="sxs-lookup"><span data-stu-id="973c7-146"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
```cpp  
      [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
public ref class PInvokeWrapper  
{  
public:  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
};  
```  
  
```csharp  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
class PInvokeWrapper  
{  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
}  
```  
  
 <span data-ttu-id="973c7-147"><xref:System.Security.Permissions.SecurityAction> Modyfikatory również działać prawidłowo w zagnieżdżonych scenariusz, w którym są umieszczane na obiekt wywołujący platformy wywołania wywołania:</span><span class="sxs-lookup"><span data-stu-id="973c7-147"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
```cpp  
      {  
public ref class PInvokeWrapper  
public:  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionDeny();  
  
    [RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
};  
```  
  
```csharp  
class PInvokeScenario  
{  
    [DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
    private static extern bool CallRegistryPermissionInternal();  
  
    [RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    public static bool CallRegistryPermission()  
    {  
     return CallRegistryPermissionInternal();  
    }  
}  
```  
  
#### <a name="com-interop-examples"></a><span data-ttu-id="973c7-148">Przykłady międzyoperacyjnego modelu COM</span><span class="sxs-lookup"><span data-stu-id="973c7-148">COM Interop Examples</span></span>  
 <span data-ttu-id="973c7-149">COM interop próbek w tej sekcji przedstawiający zastosowanie `RegistryPermission` atrybutu z modyfikatorami przeszukiwania stosu.</span><span class="sxs-lookup"><span data-stu-id="973c7-149">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="973c7-150">Ignoruj następujące deklaracje interfejsu międzyoperacyjnego COM `Assert`, `Deny`, i `PermitOnly` modyfikatory, podobnie jak platforma wywołania przykłady w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="973c7-150">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Assert, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDenyStubsItf  
{  
[RegistryPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Deny, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IAssertStubsItf  
{  
[RegistryPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.PermitOnly, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
 <span data-ttu-id="973c7-151">Ponadto `Demand` modyfikator nie jest akceptowany w scenariuszach deklaracji interfejsu międzyoperacyjnego modelu COM, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="973c7-151">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="973c7-152">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="973c7-152">See Also</span></span>  
 [<span data-ttu-id="973c7-153">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="973c7-153">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)  
 [<span data-ttu-id="973c7-154">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="973c7-154">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)  
 [<span data-ttu-id="973c7-155">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="973c7-155">Specifying a Character Set</span></span>](specifying-a-character-set.md)  
 [<span data-ttu-id="973c7-156">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="973c7-156">Platform Invoke Examples</span></span>](platform-invoke-examples.md)  
 <span data-ttu-id="973c7-157">[Zagadnienia dotyczące zabezpieczeń wywołanie platformy](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="973c7-157">[Platform Invoke Security Considerations](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))</span></span>  
 [<span data-ttu-id="973c7-158">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="973c7-158">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)  
 [<span data-ttu-id="973c7-159">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="973c7-159">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)  
 [<span data-ttu-id="973c7-160">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="973c7-160">Calling a DLL Function</span></span>](calling-a-dll-function.md)
