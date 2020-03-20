---
title: 'Porady: implementowanie funkcji wywołania zwrotnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
ms.openlocfilehash: b7aae1e70ac736d60bed1e79291235db1c220281
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181413"
---
# <a name="how-to-implement-callback-functions"></a>Porady: implementowanie funkcji wywołania zwrotnego
Poniższa procedura i przykład pokazują, jak aplikacja zarządzana, przy użyciu wywołania platformy, można wydrukować wartość dojścia dla każdego okna na komputerze lokalnym. W szczególności procedura i przykład użyć **EnumWindows** funkcji krok po kroku przez listę okien i funkcji wywołania zwrotnego zarządzanego (o nazwie CallBack) do drukowania wartości dojścia okna.  
  
### <a name="to-implement-a-callback-function"></a>Aby zaimplementować funkcję wywołania zwrotnego  
  
1. Spójrz na podpis dla funkcji **EnumWindows** przed przejściem dalej z implementacji. **EnumWindows** ma następujący podpis:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Jedną z wskazówek, że ta funkcja wymaga wywołania zwrotnego jest obecność **argumentu lpEnumFunc.** Często jest widoczny prefiks **lp** (długi wskaźnik) w połączeniu z sufiksem **Func** w nazwie argumentów, które przyjmują wskaźnik do funkcji wywołania zwrotnego. Aby uzyskać dokumentację dotyczącą funkcji win32, zobacz microsoft platform SDK.  
  
2. Utwórz zarządzał funkcją wywołania zwrotnego. W przykładzie deklaruje się `CallBack`typ delegata, wywoływany , który przyjmuje dwa argumenty (**hwnd** i **lparam**). Pierwszy argument jest dojściem do okna; drugi argument jest zdefiniowany przez aplikację. W tej wersji oba argumenty muszą być liczby całkowite.  
  
     Wywołanie zwrotne funkcje zazwyczaj zwracają wartości niezerowe, aby wskazać sukces i zero, aby wskazać błąd. W tym przykładzie jawnie ustawia wartość zwracaną **true,** aby kontynuować wyliczenie.  
  
3. Utwórz pełnomocnika i przekaż go jako argument do funkcji **EnumWindows.** Wywołanie platformy konwertuje delegata do znanego formatu wywołania zwrotnego automatycznie.  
  
4. Upewnij się, że moduł zbierający elementy bezużyteczne nie odzyskuje delegata przed zakończeniem pracy funkcji wywołania zwrotnego. Po przekazaniu delegata jako parametr lub przekazać pełnomocnika zawarte jako pole w strukturze, pozostaje niepobrane na czas trwania wywołania. Tak jak w poniższym przykładzie wyliczenia funkcja wywołania zwrotnego kończy pracę przed zwraca wywołanie i nie wymaga żadnych dodatkowych działań przez zarządzanego obiektu wywołującego.  
  
     Jeśli jednak funkcja wywołania zwrotnego może być wywoływana po powrocie wywołania, zarządzany wywołujący musi podjąć kroki, aby upewnić się, że pełnomocnik pozostaje niepobrany, dopóki funkcja wywołania zwrotnego nie zostanie zakończona. Aby uzyskać szczegółowe informacje na temat zapobiegania wyrzucania elementów bezużytecznych, zobacz [Interop marshaling](interop-marshaling.md) with Platform Invoke.  
  
## <a name="example"></a>Przykład  
  
```vb  
Imports System  
Imports System.Runtime.InteropServices  
  
Public Delegate Function CallBack( _  
hwnd As Integer, lParam As Integer) As Boolean  
  
Public Class EnumReportApp  
  
    Declare Function EnumWindows Lib "user32" ( _  
       x As CallBack, y As Integer) As Integer  
  
    Public Shared Sub Main()  
        EnumWindows(AddressOf EnumReportApp.Report, 0)  
    End Sub 'Main  
  
    Public Shared Function Report(hwnd As Integer, lParam As Integer) _  
    As Boolean  
        Console.Write("Window handle is ")  
        Console.WriteLine(hwnd)  
        Return True  
    End Function 'Report  
End Class 'EnumReportApp  
```  
  
```csharp  
using System;  
using System.Runtime.InteropServices;  
  
public delegate bool CallBack(int hwnd, int lParam);  
  
public class EnumReportApp  
{  
    [DllImport("user32")]  
    public static extern int EnumWindows(CallBack x, int y);
  
    public static void Main()
    {  
        CallBack myCallBack = new CallBack(EnumReportApp.Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    public static bool Report(int hwnd, int lParam)  
    {
        Console.Write("Window handle is ");  
        Console.WriteLine(hwnd);  
        return true;  
    }  
}  
```  
  
```cpp  
using namespace System;  
using namespace System::Runtime::InteropServices;  
  
// A delegate type.  
delegate bool CallBack(int hwnd, int lParam);  
  
// Managed type with the method to call.  
ref class EnumReport  
{  
// Report the window handle.  
public:  
    [DllImport("user32")]  
    static int EnumWindows(CallBack^ x, int y);  
  
    static void Main()  
    {  
        EnumReport^ er = gcnew EnumReport;  
        CallBack^ myCallBack = gcnew CallBack(&EnumReport::Report);  
        EnumWindows(myCallBack, 0);  
    }  
  
    static bool Report(int hwnd, int lParam)  
    {  
       Console::Write(L"Window handle is ");  
       Console::WriteLine(hwnd);  
       return true;  
    }  
};  
  
int main()  
{  
    EnumReport::Main();  
}  
```  
  
## <a name="see-also"></a>Zobacz też

- [Funkcje wywołania zwrotnego](callback-functions.md)
- [Wywołanie funkcji DLL](calling-a-dll-function.md)
