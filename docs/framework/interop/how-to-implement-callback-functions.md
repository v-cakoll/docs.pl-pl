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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e081347129ce367cf6b46ca29c07a016bb64ab95
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33389278"
---
# <a name="how-to-implement-callback-functions"></a>Porady: implementowanie funkcji wywołania zwrotnego
Poniższe procedury i przykładowe pokazują, jak wywołać przy użyciu platformy aplikacji zarządzanej, drukować wartość uchwytu dla każdego okna na komputerze lokalnym. W szczególności, użyj procedury i przykładowe **EnumWindows** funkcji kroków wykaz systemu windows oraz funkcja wywołania zwrotnego w zarządzanych (nazwane wywołania zwrotnego) do drukowania wartość uchwytu okna.  
  
### <a name="to-implement-a-callback-function"></a>Aby wdrożyć funkcję wywołania zwrotnego  
  
1.  Przyjrzyj się podpis dla **EnumWindows** funkcja przed przejściem dalej z implementacją. **EnumWindows** ma następującą sygnaturą:  
  
    ```  
    BOOL EnumWindows(WNDENUMPROC lpEnumFunc, LPARAM lParam)  
    ```  
  
     Jeden clue, że ta funkcja wymaga wywołania zwrotnego jest obecność **lpEnumFunc** argumentu. Często, aby wyświetlić **lp** prefiks (wskaźnik długi) łączony z **Func** sufiks nazwy argumentów, które przyjmują wskaźnika do funkcji wywołania zwrotnego. Dokumentacja funkcji Win32 temacie zestawu SDK platformy firmy Microsoft.  
  
2.  Utwórz funkcję wywołania zwrotnego w zarządzanych. Przykład deklaruje typ delegata o nazwie `CallBack`, który przyjmuje dwa argumenty (**hwnd** i **lparam**). Pierwszy argument jest dojścia do okna; drugi argument jest zdefiniowane przez aplikację. W tej wersji oba argumenty muszą być liczbami całkowitymi.  
  
     Funkcje wywołania zwrotnego zwracają zazwyczaj niezerowe wartości oznacza powodzenie i zera do wskazania błędu. W tym przykładzie jawnie ustawia wartość zwrotną **true** kontynuowanie wyliczenia.  
  
3.  Utworzenia delegata i przekaż go jako argument **EnumWindows** funkcji. Wywołanie platformy automatycznie konwertuje delegata do formatu znanych wywołania zwrotnego.  
  
4.  Upewnij się, że moduł zbierający elementy bezużyteczne nie odzyskać delegat ukończenia pracy funkcji wywołania zwrotnego. Przekazywanie obiektu delegate jako parametr lub przekazywanie obiektu delegate zawarte jako pola w strukturze pozostaje niepobranych na czas trwania wywołania. Tak jak w przypadku w poniższym przykładzie wyliczenie, funkcja wywołania zwrotnego nie ukończy pracy przed wywołanie zwraca i nie wymaga dodatkowych czynności przez obiekt wywołujący zarządzanych.  
  
     Jeśli jednak funkcja wywołania zwrotnego można wywołać po wywołaniu zwraca, wywołujący zarządzanych, należy wykonać kroki w celu zapewnienia delegat pozostaje niepobranych, dopóki nie zakończy się działanie funkcji wywołania zwrotnego. Aby uzyskać szczegółowe informacje dotyczące zapobiegania wyrzucanie elementów bezużytecznych, zobacz [organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md) z wywołania platformy.  
  
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
 [Funkcje wywołania zwrotnego](../../../docs/framework/interop/callback-functions.md)  
 [Wywołanie funkcji DLL](../../../docs/framework/interop/calling-a-dll-function.md)
