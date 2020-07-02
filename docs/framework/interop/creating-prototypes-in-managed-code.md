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
# <a name="creating-prototypes-in-managed-code"></a>Tworzenie prototypów w kodzie zarządzanym
W tym temacie opisano, jak uzyskać dostęp do funkcji niezarządzanych i wprowadzono kilka pól atrybutów, które umożliwiają dodawanie adnotacji do definicji metody w kodzie zarządzanym. Przykłady, które demonstrują sposób konstruowania. Deklaracje oparte na sieci, które mają być używane z wywołaniem platformy, można znaleźć w temacie [kierowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
 Aby można było uzyskać dostęp do niezarządzanej funkcji DLL z kodu zarządzanego, należy znać nazwę funkcji i nazwę biblioteki DLL, która go wyeksportuje. Korzystając z tych informacji, można rozpocząć pisanie zarządzanej definicji dla niezarządzanej funkcji, która jest zaimplementowana w bibliotece DLL. Ponadto można dostosować sposób, w jaki wywołanie platformy tworzy funkcję i kierowanie danych do i z funkcji.  
  
> [!NOTE]
> Funkcje interfejsu API systemu Windows, które przydzielą ciąg, umożliwiają zwolnienie ciągu przy użyciu metody takiej jak `LocalFree` . Wywołanie platformy obsługuje takie parametry inaczej. W przypadku wywołań wywołania platformy należy `IntPtr` zamiast typu wprowadzić parametr `String` . Użyj metod dostarczonych przez <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> klasę, aby ręcznie przekonwertować typ na ciąg i zwolnić go ręcznie.  
  
## <a name="declaration-basics"></a>Podstawowe informacje o deklaracji  
 Zarządzane definicje funkcji niezarządzanych są zależne od języka, co jest widoczne w poniższych przykładach. Aby zapoznać się z bardziej kompletnymi przykładami kodu, zobacz [przykładowe wywołania platformy](platform-invoke-examples.md).  
  
```vb
Friend Class NativeMethods
    Friend Declare Auto Function MessageBox Lib "user32.dll" (
        ByVal hWnd As IntPtr,
        ByVal lpText As String,
        ByVal lpCaption As String,
        ByVal uType As UInteger) As Integer
End Class
```
  
 Aby zastosować <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping?displayProperty=nameWithType> pola, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig?displayProperty=nameWithType> , <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError?displayProperty=nameWithType> lub <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar?displayProperty=nameWithType> do deklaracji Visual Basic, należy użyć <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu zamiast `Declare` instrukcji.  
  
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
  
## <a name="adjusting-the-definition"></a>Dostosowywanie definicji  
 Niezależnie od tego, czy ustawisz je jawnie, czy nie, pola atrybutów są w pracy definiujące zachowanie kodu zarządzanego. Wywołanie platformy działa zgodnie z wartościami domyślnymi ustawionymi w różnych polach, które istnieją jako metadane w zestawie. To zachowanie domyślne można zmienić, dostosowując wartości jednego lub kilku pól. W wielu przypadkach należy użyć, <xref:System.Runtime.InteropServices.DllImportAttribute> Aby ustawić wartość.  
  
 W poniższej tabeli przedstawiono kompletny zestaw pól atrybutów odnoszących się do wywołania platformy. Dla każdego pola tabela zawiera wartość domyślną i link do informacji na temat sposobu użycia tych pól do definiowania niezarządzanych funkcji DLL.  
  
|Pole|Opis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Włącza lub wyłącza Mapowanie najlepszego dopasowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Określa konwencję wywoływania, która ma być używana podczas przekazywania argumentów metody. Wartość domyślna to `WinAPI` , która odnosi się do `__stdcall` 32-bitowych platform opartych na procesorze Intel.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Kontroluje nazwę dekorowanie i sposób, w jaki argumenty ciągów powinny być organizowane w funkcji. Wartość domyślna to `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Określa punkt wejścia biblioteki DLL, który ma zostać wywołany.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Określa, czy punkt wejścia powinien zostać zmodyfikowany, aby odpowiadał zestawowi znaków. Wartość domyślna różni się w zależności od języka programowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Określa, czy podpis metody zarządzanej powinien być przekształcony w niezarządzany podpis, który zwraca wynik HRESULT i ma dodatkowy argument [out, retval] dla wartości zwracanej.<br /><br /> Wartość domyślna to `true` (podpis nie powinien być przekształcony).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Umożliwia wywołującemu użycie `Marshal.GetLastWin32Error` funkcji API do określenia, czy wystąpił błąd podczas wykonywania metody. W Visual Basic, wartość domyślna to `true` ; w językach C# i C++ wartość domyślna to `false` .|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Kontroluje wyrzucanie wyjątków dla znaku Unicode napotkano, który jest konwertowany na znak ANSI "?".|  
  
 Aby uzyskać szczegółowe informacje referencyjne, zobacz <xref:System.Runtime.InteropServices.DllImportAttribute> .  
  
## <a name="platform-invoke-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń wywołania platformy  
 `Assert` `Deny` `PermitOnly` Elementy członkowskie <xref:System.Security.Permissions.SecurityAction> wyliczenia są określane jako *Modyfikatory*przeszukiwania stosu. Te elementy członkowskie są ignorowane, jeśli są używane jako atrybuty deklaracyjne w deklaracjach wywołania platformy i instrukcjach języka definicji interfejsu COM (IDL).  
  
### <a name="platform-invoke-examples"></a>Przykłady wywołań platformy  
 Przykłady wywołania platformy w tej sekcji ilustrują użycie `RegistryPermission` atrybutu za pomocą modyfikatorów przeszukiwania stosu.  
  
 W poniższym przykładzie <xref:System.Security.Permissions.SecurityAction> `Assert` `Deny` `PermitOnly` modyfikatory, i są ignorowane.  
  
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
  
 Jednak `Demand` modyfikator w poniższym przykładzie zostanie zaakceptowany.  
  
```csharp
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction>Modyfikatory działają poprawnie, jeśli są umieszczone na klasie, która zawiera (zawija) wywołanie wywołania platformy.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction>Modyfikatory działają również prawidłowo w zagnieżdżonym scenariuszu, w którym są umieszczane na wywołującym wywołania wywołania platformy:  
  
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
  
#### <a name="com-interop-examples"></a>Przykłady międzyoperacyjności modelu COM  
 Przykłady międzyoperacyjności modelu COM w tej sekcji ilustrują użycie `RegistryPermission` atrybutu za pomocą modyfikatorów przeszukiwania stosu.  
  
 Poniższe deklaracje interfejsu COM międzyoperacyjnych ignorują `Assert` `Deny` modyfikatory, i, `PermitOnly` podobnie jak w przypadku wywołania platform w poprzedniej sekcji.  
  
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
  
 Ponadto `Demand` modyfikator nie jest akceptowany w scenariuszach deklaracji interfejsu COM Interop, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)
- [Określanie punktu wejścia](specifying-an-entry-point.md)
- [Określanie zestawu znaków](specifying-a-character-set.md)
- [Przykłady wywołań platformy](platform-invoke-examples.md)
- [Zagadnienia dotyczące zabezpieczeń wywołania platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md)
- [Tworzenie klasy utrzymującej funkcje DLL](creating-a-class-to-hold-dll-functions.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
