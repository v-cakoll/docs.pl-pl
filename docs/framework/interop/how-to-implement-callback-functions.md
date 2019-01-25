---
title: 'Instrukcje: Implementowanie funkcji wywołania zwrotnego'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- callback function, implementing
ms.assetid: e55b3712-b9ea-4453-bd9a-ad5cfa2f6bfa
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1bf972455aa54a7fe45ffd7858ac9e5da5eee6e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54718679"
---
# <a name="how-to-implement-callback-functions"></a>Instrukcje: Implementowanie funkcji wywołania zwrotnego
Poniższy przykład i procedury pokazują, jak wywołać przy użyciu platformy zarządzanej aplikacji, można wydrukować wartość dojścia dla każdego przedziału na komputerze lokalnym. W szczególności procedury i przykładowego użycia **EnumWindows** funkcji przechodzić przez wykaz systemu windows i funkcji wywołania zwrotnego zarządzanych (o nazwie wywołanie zwrotne) aby wyświetlić wartość uchwyt okna.  
  
### <a name="to-implement-a-callback-function"></a>Aby zaimplementować funkcję wywołania zwrotnego  
  
1.  Przyjrzyj się podpis dla **EnumWindows** funkcji przed przejściem dalej z implementacją. **EnumWindows** ma następujący podpis:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Co sugeruje, że ta funkcja wymaga wywołania zwrotnego jest obecność **lpEnumFunc** argumentu. Bardzo często, aby zobaczyć **lp** prefiksu (wskaźnik długi) w połączeniu z **Func** sufiks nazwy argumentów, które przyjmują wskaźnik do funkcji wywołania zwrotnego. Dokumentację informacji na temat funkcji Win32 na ten temat można znaleźć w zestawie SDK platformy firmy Microsoft.  
  
2.  Tworzenie funkcji wywołania zwrotnego zarządzanych. Przykład deklaruje typu delegata, o nazwie `CallBack`, który przyjmuje dwa argumenty (**hwnd** i **lparam**). Pierwszy argument jest uchwytem do okna; drugi argument funkcji jest zdefiniowany przez aplikację. W tej wersji oba argumenty muszą być liczbami całkowitymi.  
  
     Funkcje wywołania zwrotnego zazwyczaj zwraca wartość różną od zera wartości do wskazania sukcesu oraz zero, aby wskazać błąd. W tym przykładzie jawnie ustawia wartość zwracaną **true** kontynuować wyliczenia.  
  
3.  Utwórz delegata i przekazać go jako argument do **EnumWindows** funkcji. Wywołanie platformy automatycznie konwertuje delegata do formatu znanych wywołania zwrotnego.  
  
4.  Upewnij się, że moduł odśmiecania pamięci nie spowoduje odzyskania delegata przed funkcji wywołania zwrotnego nie ukończy pracy. Przekazywanie obiektu delegate jako parametr lub przekazywanie obiektu delegate zawarte jako pole w strukturze, pozostaje niepobranych na czas trwania wywołania. Tak jak w przypadku, w poniższym przykładzie wyliczenie, funkcja wywołania zwrotnego nie ukończy pracy przed wywołanie zwraca i nie wymaga dodatkowych czynności przez zarządzany obiekt wywołujący.  
  
     Jeśli jednak po wywołaniu zwraca można wywołać funkcję wywołania zwrotnego, zarządzanego obiektu wywołującego, należy wykonać czynności, aby upewnić się, delegat pozostaje niepobranych, dopóki nie zakończy się działanie funkcji wywołania zwrotnego. Aby uzyskać szczegółowe informacje dotyczące zapobiegania wyrzucania elementów bezużytecznych, zobacz [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md) za pomocą wywołania platformy.  
  
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
  
## <a name="see-also"></a>Zobacz także
- [Funkcje wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md)
- [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
