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
ms.openlocfilehash: b305158ac87f01044bae5455cea07ca3b3a2e491
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="creating-prototypes-in-managed-code"></a>Tworzenie prototypów w kodzie zarządzanym
Ten temat zawiera opis sposobu dostępu z funkcjami niezarządzanymi i wprowadzono kilka pól atrybutów, które adnotacji definicji metody w kodzie zarządzanym. Aby uzyskać przykłady pokazujące, które pokazują, jak utworzyć. Deklaracje opartych na potrzeby używania z platformy invoke, zobacz [organizowanie danych za pomocą wywołania platformy](marshaling-data-with-platform-invoke.md).  
  
 Przed uzyskaniem dostępu niezarządzanych funkcji DLL z kodu zarządzanego, musisz znać nazwę funkcji i nazwy biblioteki DLL, który eksportuje je. Dzięki tym informacjom można rozpocząć zapisu zarządzanej definicji niezarządzanej funkcji, która jest zaimplementowana w bibliotece DLL. Ponadto można dostosować sposób wywołania tej platformy tworzy funkcję i marshals danych do i z funkcji.  
  
> [!NOTE]
>  Funkcje interfejsu API Win32, które przydzielić ciągu umożliwiają wolne ciąg przy użyciu metody, takie jak `LocalFree`. Wywołanie platformy obsługuje tych parametrów w inny sposób. Dla platformy wywołania wywołania, określ parametr `IntPtr` wpisz zamiast `String` typu. Użyj metody, które są udostępniane przez <xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType> klasę, aby przekonwertować na ciąg typu ręcznie i zwolnij go ręcznie.  
  
## <a name="declaration-basics"></a>Podstawy deklaracji  
 Definicje zarządzanych do niezarządzanych funkcji są zależne od języka, jak to pokazano w poniższych przykładach. Aby uzyskać bardziej szczegółowy przykłady kodu, zobacz [przykłady wywołania platformy](platform-invoke-examples.md).  
  
```vb  
Imports System.Runtime.InteropServices  
Public Class Win32  
    Declare Auto Function MessageBox Lib "user32.dll" _  
       (ByVal hWnd As Integer, _  
        ByVal txt As String, ByVal caption As String, _  
        ByVal Typ As Integer) As IntPtr  
End Class  
```  
  
 Aby zastosować <xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>, <xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>, <xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>, <xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>, <xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>, lub <xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar> pól do [!INCLUDE[vbprvbext](../../../includes/vbprvbext-md.md)] deklaracji, należy użyć <xref:System.Runtime.InteropServices.DllImportAttribute> atrybutu zamiast `Declare` instrukcji.  
  
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
 Czy zostaną ustawione jawnie lub nie, atrybutu pola są w miejscu pracy Definiowanie zachowania kodu zarządzanego. Wywołanie platformy działa zgodnie z wartościami domyślnymi, ustawiać różne pola, które istnieją jak metadanych w zestawie. To zachowanie domyślne można zmienić, dopasowując wartości co najmniej jedno pole. W wielu przypadkach można użyć <xref:System.Runtime.InteropServices.DllImportAttribute> można ustawić wartości.  
  
 W poniższej tabeli wymieniono pełny zestaw atrybut, który pola, które odnoszą się do platformy wywołaniu. Dla każdego pola w tabeli przedstawiono wartości domyślnej i łącze do informacji na temat korzystania z tych pól do definiowania niezarządzanych funkcji DLL.  
  
|Pole|Opis|  
|-----------|-----------------|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.BestFitMapping>|Włącza lub wyłącza mapowanie najlepszego dopasowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CallingConvention>|Określa konwencję wywołania do użycia w przekazywanie argumentów metody. Wartość domyślna to `WinAPI`, które odpowiada `__stdcall` na platformach opartych na Intel 32-bitowych.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.CharSet>|Przekręcona nazwa kontrolki i sposób, w jaki argumenty ciągu powinny być przekazywane do funkcji. Wartość domyślna to `CharSet.Ansi`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.EntryPoint>|Określa punkt wejścia biblioteki DLL do wywołania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ExactSpelling>|Określa, czy punkt wejścia powinien być modyfikowany odpowiadać zestaw znaków. Wartość domyślna zależy od języka programowania.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.PreserveSig>|Określa, czy transformacji podpis metody zarządzane do niezarządzanego podpisu, która zwraca HRESULT i ma dodatkowe [out, retval] argument dla wartości zwracanej.<br /><br /> Wartość domyślna to `true` (podpis nie powinien zostać przekształcone).|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.SetLastError>|Obiekt wywołujący, aby użyć umożliwia `Marshal.GetLastWin32Error` funkcja interfejsu API w celu ustalenia, czy wystąpił błąd podczas wykonywania metody. W języku Visual Basic, wartość domyślna to `true`; w języku C# i C++, wartość domyślna to `false`.|  
|<xref:System.Runtime.InteropServices.DllImportAttribute.ThrowOnUnmappableChar>|Formanty Zgłaszanie wyjątku na zmapować znak Unicode, który jest konwertowany na ANSI "?" znaków.|  
  
 Aby uzyskać szczegółowe informacje, zobacz <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
## <a name="platform-invoke-security-considerations"></a>Zagadnienia dotyczące zabezpieczeń wywołanie platformy  
 `Assert`, `Deny`, I `PermitOnly` członkami <xref:System.Security.Permissions.SecurityAction> wyliczenia są określane jako *Modyfikatory przeszukiwania stosu*. Elementy te są ignorowane, jeśli są używane jako deklaratywne atrybuty na platformie wywołania deklaracje i oświadczenia języka definicji interfejsu COM (IDL).  
  
### <a name="platform-invoke-examples"></a>Przykłady wywołań platformy  
 Wywołanie platformy próbek w tej sekcji przedstawiający zastosowanie `RegistryPermission` atrybutu z modyfikatorami przeszukiwania stosu.  
  
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
  
 Jednak `Demand` modyfikator w poniższym przykładzie jest akceptowany.  
  
```  
[DllImport("MyClass.dll", EntryPoint = "CallRegistryPermission")]  
[RegistryPermission(SecurityAction.Demand, Unrestricted = true)]  
    private static extern bool CallRegistryPermissionDeny();  
```  
  
 <xref:System.Security.Permissions.SecurityAction> Modyfikatory działają prawidłowo, jeśli zostały one umieszczone na klasę, która zawiera (zawija) platformy wywołaniem.  
  
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
  
 <xref:System.Security.Permissions.SecurityAction> Modyfikatory również działać prawidłowo w zagnieżdżonych scenariusz, w którym są umieszczane na obiekt wywołujący platformy wywołania wywołania:  
  
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
 COM interop próbek w tej sekcji przedstawiający zastosowanie `RegistryPermission` atrybutu z modyfikatorami przeszukiwania stosu.  
  
 Ignoruj następujące deklaracje interfejsu międzyoperacyjnego COM `Assert`, `Deny`, i `PermitOnly` modyfikatory, podobnie jak platforma wywołania przykłady w poprzedniej sekcji.  
  
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
  
 Ponadto `Demand` modyfikator nie jest akceptowany w scenariuszach deklaracji interfejsu międzyoperacyjnego modelu COM, jak pokazano w poniższym przykładzie.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 [Wykorzystywanie niezarządzanych funkcji DLL](consuming-unmanaged-dll-functions.md)  
 [Określanie punktu wejścia](specifying-an-entry-point.md)  
 [Określanie zestawu znaków](specifying-a-character-set.md)  
 [Przykłady wywołań platformy](platform-invoke-examples.md)  
 [Zagadnienia dotyczące zabezpieczeń wywołanie platformy](https://msdn.microsoft.com/library/bbcc67f7-50b5-4917-88ed-cb15470409fb(v=vs.100))  
 [Identyfikowanie funkcji w bibliotekach DLL](identifying-functions-in-dlls.md)  
 [Tworzenie klasy utrzymującej funkcje DLL](creating-a-class-to-hold-dll-functions.md)  
 [Wywołanie funkcji DLL](calling-a-dll-function.md)
