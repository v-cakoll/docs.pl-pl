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
Poniższa procedura i przykład przedstawiają sposób, w jaki aplikacja zarządzana używająca funkcji wywołania platformy może drukować wartość dojścia dla każdego okna na komputerze lokalnym. W ramach procedury i przykładu Użyj funkcji **EnumWindows** , aby przejść przez listę systemu Windows i zarządzaną funkcję wywołania zwrotnego (nazwanego wywołania zwrotnego) w celu wydrukowania wartości uchwytu okna.  
  
### <a name="to-implement-a-callback-function"></a>Aby zaimplementować funkcję wywołania zwrotnego  
  
1. Przed przejściem do implementacji zapoznaj się z podpisem funkcji **EnumWindows** . **EnumWindows** ma następujący podpis:  
  
    ```cpp
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)
    ```
  
     Jedną z wskazówek, że ta funkcja wymaga wywołania zwrotnego, jest obecność argumentu **lpEnumFunc** . Często widzisz prefiks **LP** (długi wskaźnik) połączony z sufiksem **Func** w nazwie argumentów, które przyjmują wskaźnik do funkcji wywołania zwrotnego. Aby uzyskać dokumentację dotyczącą funkcji Win32, zobacz zestaw SDK platformy Microsoft.  
  
2. Utwórz zarządzaną funkcję wywołania zwrotnego. Przykład deklaruje typ delegata o nazwie `CallBack`, który przyjmuje dwa argumenty (**HWND** i **lParam**). Pierwszy argument jest dojściem do okna; drugi argument jest zdefiniowany przez aplikację. W tej wersji oba argumenty muszą być liczbami całkowitymi.  
  
     Funkcje wywołania zwrotnego zwykle zwracają wartości niezerowe, aby wskazać sukces i zero, aby wskazać błąd. Ten przykład jawnie ustawia wartość zwracaną na **true** , aby kontynuować wyliczanie.  
  
3. Utwórz delegata i przekaż go jako argument do funkcji **EnumWindows** . Wywołanie platformy konwertuje delegata na automatycznie znany Format wywołania zwrotnego.  
  
4. Upewnij się, że moduł zbierający elementy bezużyteczne nie odzyska delegata, zanim funkcja wywołania zwrotnego zakończy pracę. Gdy przekazujesz delegata jako parametr lub Przekaż delegata zawarty jako pole w strukturze, pozostanie ono niezebrane na czas trwania wywołania. Tak więc, podobnie jak w poniższym przykładzie wyliczenia, funkcja wywołania zwrotnego uzupełnia swoją pracę przed wywołaniem zwrotnym i nie wymaga żadnych dodatkowych akcji przez zarządzany obiekt wywołujący.  
  
     Jeśli jednak funkcja wywołania zwrotnego może być wywoływana po wywołaniu zwrotnym, zarządzany obiekt wywołujący musi wykonać kroki, aby upewnić się, że delegat pozostanie niepobrany do momentu zakończenia funkcji wywołania zwrotnego. Aby uzyskać szczegółowe informacje na temat zapobiegania wyrzucaniu elementów bezużytecznych, zobacz [Marshaling Interop](interop-marshaling.md) with platform Invoke.  
  
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
