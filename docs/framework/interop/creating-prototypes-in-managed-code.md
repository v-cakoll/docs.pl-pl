---
title: Tworzenie prototypów w kodzie zarządzanym
description: Tworzenie prototypów w kodzie zarządzanym .NET, aby można było uzyskać dostęp do funkcji niezarządzanych i użyć pól atrybutów, które dodają adnotację do definicji metody w kodzie zarządzanym.
ms.date: 03/30/2017
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
ms.openlocfilehash: 76b1a87c4513fdee21c5c3d5eba533b11e022e3a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622162"
---
# <a name="creating-prototypes-in-managed-code"></a><span data-ttu-id="05bce-103">Tworzenie prototypów w kodzie zarządzanym</span><span class="sxs-lookup"><span data-stu-id="05bce-103">Creating Prototypes in Managed Code</span></span>
<span data-ttu-id="05bce-104">W tym temacie opisano, jak uzyskać dostęp do funkcji niezarządzanych i wprowadzono kilka pól atrybutów, które umożliwiają dodawanie adnotacji do definicji metody w kodzie zarządzanym.</span><span class="sxs-lookup"><span data-stu-id="05bce-104">This topic describes how to access unmanaged functions and introduces several attribute fields that annotate method definition in managed code.</span></span> <span data-ttu-id="05bce-105">Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).</span><span class="sxs-lookup"><span data-stu-id="05bce-105">For examples that demonstrate how to construct .NET-based declarations to be used with platform invoke, see [Marshaling Data with Platform Invoke](marshaling-data-with-platform-invoke.md).</span></span>  
  
 <span data-ttu-id="05bce-106">Aby można było uzyskać dostęp do niezarządzanej funkcji DLL z kodu zarządzanego, należy znać nazwę funkcji i nazwę biblioteki DLL, która go wyeksportuje.</span><span class="sxs-lookup"><span data-stu-id="05bce-106">Before you can access an unmanaged DLL function from managed code, you need to know the name of the function and the name of the DLL that exports it.</span></span> <span data-ttu-id="05bce-107">Korzystając z tych informacji, można rozpocząć pisanie zarządzanej definicji dla niezarządzanej funkcji, która jest zaimplementowana w bibliotece DLL.</span><span class="sxs-lookup"><span data-stu-id="05bce-107">With this information, you can begin to write the managed definition for an unmanaged function that is implemented in a DLL.</span></span> <span data-ttu-id="05bce-108">Ponadto można dostosować sposób, w jaki wywołanie platformy tworzy funkcję i kierowanie danych do i z funkcji.</span><span class="sxs-lookup"><span data-stu-id="05bce-108">Furthermore, you can adjust the way that platform invoke creates the function and marshals data to and from the function.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="05bce-109">Funkcje interfejsu API systemu Windows, które przydzielą ciąg, umożliwiają zwolnienie ciągu przy użyciu metody takiej jak `LocalFree` .</span><span class="sxs-lookup"><span data-stu-id="05bce-109">Windows API functions that allocate a string enable you to free the string by using a method such as `LocalFree`.</span></span> <span data-ttu-id="05bce-110">Wywołanie platformy obsługuje takie parametry inaczej.</span><span class="sxs-lookup"><span data-stu-id="05bce-110">Platform invoke handles such parameters differently.</span></span> <span data-ttu-id="05bce-111">W przypadku wywołań wywołania platformy należy `IntPtr` zamiast typu wprowadzić parametr `String` .</span><span class="sxs-lookup"><span data-stu-id="05bce-111">For platform invoke calls, make the parameter an `IntPtr` type instead of a `String` type.</span></span> <span data-ttu-id="05bce-112">Użyj metod dostarczonych przez <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> klasę, aby ręcznie przekonwertować typ na ciąg i zwolnić go ręcznie.</span><span class="sxs-lookup"><span data-stu-id="05bce-112">Use methods that are provided by the <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> class to convert the type to a string manually and free it manually.</span></span>  
  
## <a name="declaration-basics"></a><span data-ttu-id="05bce-113">Podstawowe informacje o deklaracji</span><span class="sxs-lookup"><span data-stu-id="05bce-113">Declaration Basics</span></span>  
 <span data-ttu-id="05bce-114">Zarządzane definicje funkcji niezarządzanych są zależne od języka, co jest widoczne w poniższych przykładach.</span><span class="sxs-lookup"><span data-stu-id="05bce-114">Managed definitions to unmanaged functions are language-dependent, as you can see in the following examples.</span></span> <span data-ttu-id="05bce-115">Aby zapoznać się z bardziej kompletnymi przykładami kodu, zobacz [przykładowe wywołania platformy](platform-invoke-examples.md).</span><span class="sxs-lookup"><span data-stu-id="05bce-115">For more complete code examples, see [Platform Invoke Examples](platform-invoke-examples.md).</span></span>  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 <span data-ttu-id="05bce-116">Aby zastosować <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> pola, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> do deklaracji Visual Basic, należy użyć <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu zamiast `Declare` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="05bce-116">To apply the <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType>, or <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> fields to a Visual Basic declaration, you must use the <xref:System.Runtime.InteropServices.DllImportAttribute> attribute instead of the `Declare` statement.</span></span>  
  
```vb
Imports System.Runtime.InteropServices

Friend Class NativeMethods
    <DllImport("user32.dll", CharSet:=CharSet.Auto)>
    Friend Shared Function MessageBox(
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
    End Function
End Class
```
  
```csharp
using System;
using System.Runtime.InteropServices;

internal static class NativeMethods
{
    [DllImport("user32.dll")]
    internal static extern int MessageBox(
        IntPtr hWnd, string lpText, string lpCaption, uint uType);
}
```
  
```cpp
using namespace System;
using namespace System::Runtime::InteropServices;

[DllImport("user32.dll")]
extern "C" int MessageBox(
    IntPtr hWnd, String* lpText, String* lpCaption, unsigned int uType);
```
  
## <a name="adjusting-the-definition"></a><span data-ttu-id="05bce-117">Dostosowywanie definicji</span><span class="sxs-lookup"><span data-stu-id="05bce-117">Adjusting the Definition</span></span>  
 <span data-ttu-id="05bce-118">Niezależnie od tego, czy ustawisz je jawnie, czy nie, pola atrybutów są w pracy definiujące zachowanie kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="05bce-118">Whether you set them explicitly or not, attribute fields are at work defining the behavior of managed code.</span></span> <span data-ttu-id="05bce-119">Wywołanie platformy działa zgodnie z wartościami domyślnymi ustawionymi w różnych polach, które istnieją jako metadane w zestawie.</span><span class="sxs-lookup"><span data-stu-id="05bce-119">Platform invoke operates according to the default values set on various fields that exist as metadata in an assembly.</span></span> <span data-ttu-id="05bce-120">To zachowanie domyślne można zmienić, dostosowując wartości jednego lub kilku pól.</span><span class="sxs-lookup"><span data-stu-id="05bce-120">You can alter this default behavior by adjusting the values of one or more fields.</span></span> <span data-ttu-id="05bce-121">W wielu przypadkach należy użyć, <xref:System.Runtime.InteropServices.DllImportAttribute> Aby ustawić wartość.</span><span class="sxs-lookup"><span data-stu-id="05bce-121">In many cases, you use the <xref:System.Runtime.InteropServices.DllImportAttribute> to set a value.</span></span>  
  
 <span data-ttu-id="05bce-122">W poniższej tabeli przedstawiono kompletny zestaw pól atrybutów odnoszących się do wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="05bce-122">The following table lists the complete set of attribute fields that pertain to platform invoke.</span></span> <span data-ttu-id="05bce-123">Dla każdego pola tabela zawiera wartość domyślną i link do informacji na temat sposobu użycia tych pól do definiowania niezarządzanych funkcji DLL.</span><span class="sxs-lookup"><span data-stu-id="05bce-123">For each field, the table includes the default value and a link to information on how to use these fields to define unmanaged DLL functions.</span></span>  
  
|<span data-ttu-id="05bce-124">Pole</span><span class="sxs-lookup"><span data-stu-id="05bce-124">Field</span></span>|<span data-ttu-id="05bce-125">Opis</span><span class="sxs-lookup"><span data-stu-id="05bce-125">Description</span></span>|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|<span data-ttu-id="05bce-126">Włącza lub wyłącza Mapowanie najlepszego dopasowania.</span><span class="sxs-lookup"><span data-stu-id="05bce-126">Enables or disables best-fit mapping.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|<span data-ttu-id="05bce-127">Określa konwencję wywoływania, która ma być używana podczas przekazywania argumentów metody.</span><span class="sxs-lookup"><span data-stu-id="05bce-127">Specifies the calling convention to use in passing method arguments.</span></span> <span data-ttu-id="05bce-128">Wartość domyślna to `WinAPI` , która odnosi się do `__stdcall` 32-bitowych platform opartych na procesorze Intel.</span><span class="sxs-lookup"><span data-stu-id="05bce-128">The default is `WinAPI`, which corresponds to `__stdcall` for the 32-bit Intel-based platforms.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|<span data-ttu-id="05bce-129">Kontroluje nazwę dekorowanie i sposób, w jaki argumenty ciągów powinny być organizowane w funkcji.</span><span class="sxs-lookup"><span data-stu-id="05bce-129">Controls name mangling and the way that string arguments should be marshaled to the function.</span></span> <span data-ttu-id="05bce-130">Wartość domyślna to `CharSet.Ansi`.</span><span class="sxs-lookup"><span data-stu-id="05bce-130">The default is `CharSet.Ansi`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|<span data-ttu-id="05bce-131">Określa punkt wejścia biblioteki DLL, który ma zostać wywołany.</span><span class="sxs-lookup"><span data-stu-id="05bce-131">Specifies the DLL entry point to be called.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|<span data-ttu-id="05bce-132">Określa, czy punkt wejścia powinien zostać zmodyfikowany, aby odpowiadał zestawowi znaków.</span><span class="sxs-lookup"><span data-stu-id="05bce-132">Controls whether an entry point should be modified to correspond to the character set.</span></span> <span data-ttu-id="05bce-133">Wartość domyślna różni się w zależności od języka programowania.</span><span class="sxs-lookup"><span data-stu-id="05bce-133">The default value varies by programming language.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|<span data-ttu-id="05bce-134">Określa, czy podpis metody zarządzanej powinien być przekształcony w niezarządzany podpis, który zwraca wynik HRESULT i ma dodatkowy argument [out, retval] dla wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="05bce-134">Controls whether the managed method signature should be transformed into an unmanaged signature that returns an HRESULT and has an additional [out, retval] argument for the return value.</span></span><br /><br /> <span data-ttu-id="05bce-135">Wartość domyślna to `true` (podpis nie powinien być przekształcony).</span><span class="sxs-lookup"><span data-stu-id="05bce-135">The default is `true` (the signature should not be transformed).</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|<span data-ttu-id="05bce-136">Umożliwia wywołującemu użycie `Marshal.GetLastWin32Error` funkcji API do określenia, czy wystąpił błąd podczas wykonywania metody.</span><span class="sxs-lookup"><span data-stu-id="05bce-136">Enables the caller to use the `Marshal.GetLastWin32Error` API function to determine whether an error occurred while executing the method.</span></span> <span data-ttu-id="05bce-137">W Visual Basic, wartość domyślna to `true` ; w językach C# i C++ wartość domyślna to `false` .</span><span class="sxs-lookup"><span data-stu-id="05bce-137">In Visual Basic, the default is `true`; in C# and C++, the default is `false`.</span></span>|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|<span data-ttu-id="05bce-138">Kontroluje wyrzucanie wyjątków dla znaku Unicode napotkano, który jest konwertowany na znak ANSI "?".</span><span class="sxs-lookup"><span data-stu-id="05bce-138">Controls throwing of an exception on an unmappable Unicode character that is converted to an ANSI "?" character.</span></span>|  
  
 <span data-ttu-id="05bce-139">Aby uzyskać szczegółowe informacje referencyjne, zobacz <xref:System.Runtime.InteropServices.DllImportAttribute> .</span><span class="sxs-lookup"><span data-stu-id="05bce-139">For detailed reference information, see <xref:System.Runtime.InteropServices.DllImportAttribute>.</span></span>  
  
## <a name="platform-invoke-security-considerations"></a><span data-ttu-id="05bce-140">Zagadnienia dotyczące zabezpieczeń wywołania platformy</span><span class="sxs-lookup"><span data-stu-id="05bce-140">Platform invoke security considerations</span></span>  
 <span data-ttu-id="05bce-141">`Assert` `Deny` `PermitOnly` Elementy członkowskie <xref:System.Security.Permissions.SecurityAction> wyliczenia są określane jako *Modyfikatory*przeszukiwania stosu.</span><span class="sxs-lookup"><span data-stu-id="05bce-141">The `Assert`, `Deny`, and `PermitOnly` members of the <xref:System.Security.Permissions.SecurityAction> enumeration are referred to as *stack walk modifiers*.</span></span> <span data-ttu-id="05bce-142">Te elementy członkowskie są ignorowane, jeśli są używane jako atrybuty deklaracyjne w deklaracjach wywołania platformy i instrukcjach języka definicji interfejsu COM (IDL).</span><span class="sxs-lookup"><span data-stu-id="05bce-142">These members are ignored if they are used as declarative attributes on platform invoke declarations and COM Interface Definition Language (IDL) statements.</span></span>  
  
### <a name="platform-invoke-examples"></a><span data-ttu-id="05bce-143">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="05bce-143">Platform Invoke Examples</span></span>  
 <span data-ttu-id="05bce-144">Przykłady wywołania platformy w tej sekcji ilustrują użycie `RegistryPermission` atrybutu za pomocą modyfikatorów przeszukiwania stosu.</span><span class="sxs-lookup"><span data-stu-id="05bce-144">The platform invoke samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="05bce-145">W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> `Assert` `Deny` `PermitOnly` modyfikatory, i są ignorowane.</span><span class="sxs-lookup"><span data-stu-id="05bce-145">In the following example, the <xref:System.Security.Permissions.SecurityAction>`Assert`, `Deny`, and `PermitOnly` modifiers are ignored.</span></span>  
  
```csharp  
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
  
 <span data-ttu-id="05bce-146">Jednak `Demand` modyfikator w poniższym przykładzie zostanie zaakceptowany.</span><span class="sxs-lookup"><span data-stu-id="05bce-146">However, the `Demand` modifier in the following example is accepted.</span></span>  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <span data-ttu-id="05bce-147"><xref:System.Security.Permissions.SecurityAction>Modyfikatory działają poprawnie, jeśli są umieszczone na klasie, która zawiera (zawija) wywołanie wywołania platformy.</span><span class="sxs-lookup"><span data-stu-id="05bce-147"><xref:System.Security.Permissions.SecurityAction> modifiers do work correctly if they are placed on a class that contains (wraps) the platform invoke call.</span></span>  
  
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
  
 <span data-ttu-id="05bce-148"><xref:System.Security.Permissions.SecurityAction>Modyfikatory działają również prawidłowo w zagnieżdżonym scenariuszu, w którym są umieszczane na wywołującym wywołania wywołania platformy:</span><span class="sxs-lookup"><span data-stu-id="05bce-148"><xref:System.Security.Permissions.SecurityAction> modifiers also work correctly in a nested scenario where they are placed on the caller of the platform invoke call:</span></span>  
  
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
  
#### <a name="com-interop-examples"></a><span data-ttu-id="05bce-149">Przykłady międzyoperacyjności modelu COM</span><span class="sxs-lookup"><span data-stu-id="05bce-149">COM Interop Examples</span></span>  
 <span data-ttu-id="05bce-150">Przykłady międzyoperacyjności modelu COM w tej sekcji ilustrują użycie `RegistryPermission` atrybutu za pomocą modyfikatorów przeszukiwania stosu.</span><span class="sxs-lookup"><span data-stu-id="05bce-150">The COM interop samples in this section illustrate the use of the `RegistryPermission` attribute with the stack walk modifiers.</span></span>  
  
 <span data-ttu-id="05bce-151">Poniższe deklaracje interfejsu COM międzyoperacyjnych ignorują `Assert` `Deny` modyfikatory, i, `PermitOnly` podobnie jak w przypadku wywołania platform w poprzedniej sekcji.</span><span class="sxs-lookup"><span data-stu-id="05bce-151">The following COM interop interface declarations ignore the `Assert`, `Deny`, and `PermitOnly` modifiers, similarly to the platform invoke examples in the previous section.</span></span>  
  
```csharp
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
  
 <span data-ttu-id="05bce-152">Ponadto `Demand` modyfikator nie jest akceptowany w scenariuszach deklaracji interfejsu COM Interop, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05bce-152">Additionally, the `Demand` modifier is not accepted in COM interop interface declaration scenarios, as shown in the following example.</span></span>  
  
```csharp  
[ComImport, Guid("12345678-43E6-43c9-9A13-47F40B338DE0")]  
interface IDemandStubsItf  
{  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallRegistryPermission();  
[FileIOPermission(SecurityAction.Demand, Unrestricted = true)]  
    bool CallFileIoPermission();  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="05bce-153">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="05bce-153">See also</span></span>

- [<span data-ttu-id="05bce-154">Wykorzystywanie niezarządzanych funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="05bce-154">Consuming Unmanaged DLL Functions</span></span>](consuming-unmanaged-dll-functions.md)
- [<span data-ttu-id="05bce-155">Określanie punktu wejścia</span><span class="sxs-lookup"><span data-stu-id="05bce-155">Specifying an Entry Point</span></span>](specifying-an-entry-point.md)
- [<span data-ttu-id="05bce-156">Określanie zestawu znaków</span><span class="sxs-lookup"><span data-stu-id="05bce-156">Specifying a Character Set</span></span>](specifying-a-character-set.md)
- [<span data-ttu-id="05bce-157">Przykłady wywołań platformy</span><span class="sxs-lookup"><span data-stu-id="05bce-157">Platform Invoke Examples</span></span>](platform-invoke-examples.md)
- <span data-ttu-id="05bce-158">[Zagadnienia dotyczące zabezpieczeń wywołania platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="05bce-158">[Platform Invoke Security Considerations](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))</span></span>
- [<span data-ttu-id="05bce-159">Identyfikowanie funkcji w bibliotekach DLL</span><span class="sxs-lookup"><span data-stu-id="05bce-159">Identifying Functions in DLLs</span></span>](identifying-functions-in-dlls.md)
- [<span data-ttu-id="05bce-160">Tworzenie klasy utrzymującej funkcje DLL</span><span class="sxs-lookup"><span data-stu-id="05bce-160">Creating a Class to Hold DLL Functions</span></span>](creating-a-class-to-hold-dll-functions.md)
- [<span data-ttu-id="05bce-161">Wywołanie funkcji DLL</span><span class="sxs-lookup"><span data-stu-id="05bce-161">Calling a DLL Function</span></span>](calling-a-dll-function.md)
