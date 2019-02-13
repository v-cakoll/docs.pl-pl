---
title: Tworzenie prototypów w kodzie zarządzanym
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6ad93144dcb56d60f9aa688400918218ef8171df
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/13/2019
ms.locfileid: "56219571"
---
# <a name="creating-prototypes-in-managed-code"></a>Tworzenie prototypów w kodzie zarządzanym
W tym temacie opisano, jak dostęp do funkcji niezarządzanych i wprowadza kilka pól atrybutów, które dodawać adnotacje do definicji metody w kodzie zarządzanym. Aby uzyskać przykłady pokazujące, jak utworzyć. Na podstawie NET deklaracje do użycia z platformą wywołania, zobacz [Marshaling danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
 Przed uzyskujesz dostęp do niezarządzanych funkcji DLL z kodu zarządzanego, musisz znać nazwę funkcji i nazwę pliku dll, który eksportuje go. Dzięki tym informacjom można rozpocząć zapisu zarządzanych definicji niezarządzanej funkcji, która jest zaimplementowana w bibliotece DLL. Ponadto, można dopasować sposób wywołania tej platformy tworzy funkcję i kieruje dane do i z funkcji.  
  
> [!NOTE]
>  Funkcji Win32 API, które alokują ciąg umożliwiają bezpłatne ciągu przy użyciu metody takie jak `LocalFree`. Wywołanie platformy obsługuje takie parametry w inny sposób. Wywołania platformy, należy parametr `IntPtr` wpisz zamiast `String` typu. Użyj metod, które są dostarczane przez <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> klasy w celu konwersji typu do ciągu ręcznie i bezpłatne go ręcznie.  
  
## <a name="declaration-basics"></a>Podstawowe informacje dotyczące deklaracji  
 Definicje zarządzanych z funkcjami niezarządzanymi są zależne od języka, jak pokazano w poniższych przykładach. Bardziej kompletny przykłady kodu, zobacz [przykłady wywoływania platformy](platform-invoke-examples.md).  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 Aby zastosować <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, lub <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> polom [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] deklaracji, należy użyć <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu zamiast `Declare` instrukcji.  
  
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
  
## <a name="adjusting-the-definition"></a>Dostosowywanie definicji  
 Czy zostaną ustawione jawnie lub nie, atrybutu pola znajdują się na pracy definiująca zachowanie kodu zarządzanego. Wywołanie platformy działa zgodnie z wartościami domyślnymi nastavit różnych pól, które istnieją jako metadane w zestawie. To zachowanie domyślne można zmodyfikować, dopasowując wartości co najmniej jednego pola. W wielu przypadkach użycia <xref:System.Runtime.InteropServices.DllImportAttribute> można ustawić wartości.  
  
 W poniższej tabeli wymieniono kompletny zestaw atrybutu pola, które odnoszą się do platformy wywołaniu. Dla każdego pola w tabeli przedstawiono wartości domyślne i łącza do informacji na temat sposobu używania tych pól do zdefiniowania niezarządzanych funkcji DLL.  
  
|Pole|Opis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Włącza lub wyłącza mapowanie najlepszego dopasowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Określa konwencję wywołania do użycia w przekazując argumenty metody. Wartość domyślna to `WinAPI`, która odnosi się do `__stdcall` na platformach opartych na architekturze Intel 32-bitowych.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Przekręcaniu nazwy kontrolki i sposób, w jaki ciąg argumenty powinny być wprowadzane do funkcji. Wartość domyślna to `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Określa punkt wejścia biblioteki DLL, który ma zostać wywołana.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Określa, czy punkt wejścia powinny zostać zmodyfikowane w celu odnoszą się do zestawu znaków. Wartość domyślna jest zależna od języka programowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Określa, czy podpis metody zarządzane powinny zostać przekształcone do niezarządzanego podpisu, który zwraca wartość HRESULT i ma dodatkowe [out, retval] argument dla wartości zwracanej.<br /><br /> Wartość domyślna to `true` (podpis nie powinny zostać przekształcone).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Włącza obiekt wywołujący, aby użyć `Marshal.GetLastWin32Error` funkcji interfejsu API w celu ustalenia, czy wystąpił błąd podczas wykonywania metody. W języku Visual Basic, wartość domyślna to `true`; w C# i C++, wartość domyślna to `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Kontroluje zgłaszania wyjątków, na którego nie można zmapować znak Unicode, który jest konwertowany na ANSI "?" znaków.|  
  
 Aby uzyskać szczegółowe informacje, zobacz <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń wywołania platformy  
 `Assert`, `Deny`, I `PermitOnly` członkowie <xref:System.Security.Permissions.SecurityAction> wyliczenia są określane jako *Modyfikatory przeszukiwania stosu*. Te elementy członkowskie są ignorowane, jeśli są one używane jako deklaratywne atrybuty na platformie wywołania deklaracje i instrukcje języka definicji interfejsu COM (IDL).  
  
### <a name="platform-invoke-examples"></a>Przykłady wywołań platformy  
 Wywołanie platformy próbek w tej sekcji pokazują korzystanie z `RegistryPermission` atrybutu z modyfikatorów przeszukiwania stosu.  
  
 W poniższym przykładzie kodu <xref:System.Security.Permissions.SecurityAction> `Assert`, `Deny`, i `PermitOnly` Modyfikatory są ignorowane.  
  
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
  
 Jednak `Demand` modyfikator w poniższym przykładzie jest akceptowane.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> Modyfikatory działać poprawnie, jeśli zostały one umieszczone w klasie, która zawiera (zawija) platformy wywołaniem.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> Modyfikatory również działają prawidłowo w zagnieżdżonych scenariusz, w którym są umieszczane na obiekcie wywołującym platformy wywołania wywołania:  
  
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
  
#### <a name="com-interop-examples"></a>Przykłady międzyoperacyjnego modelu COM  
 Przykłady międzyoperacyjnego modelu COM w tej sekcji pokazują korzystanie z `RegistryPermission` atrybutu z modyfikatorów przeszukiwania stosu.  
  
 Ignoruj następujące deklaracje międzyoperacyjności interfejsu COM `Assert`, `Deny`, i `PermitOnly` modyfikatorów, podobnie jak platforma wywołania przykładów w poprzedniej sekcji.  
  
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
  
 Ponadto `Demand` modyfikator nie jest akceptowana w scenariuszach deklaracji interfejsu międzyoperacyjnego modelu COM, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)
- [Określanie punktu wejścia](specifying-an-entry-point.md)
- [Określanie zestawu znaków](specifying-a-character-set.md)
- [Przykłady wywołań platformy](platform-invoke-examples.md)
- [Zagadnienia dotyczące zabezpieczeń wywołania platformy](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/bb397754(v=vs.100))
- [Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md)
- [Tworzenie klasy utrzymującej funkcje DLL](creating-a-class-to-hold-dll-functions.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
