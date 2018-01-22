---
title: "Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- Windows functions [Visual Basic], calling
- unsigned data types [Visual Basic]
- UShort data type [Visual Basic], using
- functions [Visual Basic], calling Windows functions
- ULong data type [Visual Basic], using
- UInteger data type [Visual Basic], using
- data types [Visual Basic], using
- unsigned types [Visual Basic]
- data types [Visual Basic], unsigned
- data types [Visual Basic], numeric
- unsigned types [Visual Basic], using
ms.assetid: c2c0e712-8dc2-43b9-b4c6-345fbb02e7ce
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 78e6789e7def5deeb8394e3aefecfdc187ec6ef6
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)
Zużywają klasy, modułu lub struktury, która ma elementów członkowskich typu Liczba całkowita bez znaku, można przejść do tych elementów członkowskich z [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)].  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Wywoływanie funkcji Windows wykorzystującej typu bez znaku  
  
1.  Użyj [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) mówić [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] biblioteki, który zawiera funkcję, jego nazwa jest w tej bibliotece jest jego sekwencja wywoływania i sposób konwertowania ciągów podczas wywoływania metody go.  
  
2.  W `Declare` instrukcji, użyj `UInteger`, `ULong`, `UShort`, lub `Byte` odpowiednio dla każdego parametru z typu bez znaku.  
  
3.  Zajrzyj do dokumentacji wywoływany można znaleźć nazwy i wartości stałe, który używa funkcji systemu Windows. Wiele z tych są zdefiniowane w pliku WinUser.h.  
  
4.  Deklarowanie stałych niezbędne w kodzie. Wiele stałe systemu Windows są wartościami typu unsigned 32-bitowe i należy je określić `As``UInteger`.  
  
5.  Wywołanie funkcji w zwykły sposób. Poniższy przykład wywołuje funkcję Windows `MessageBox`, który przyjmuje argument liczby całkowitej bez znaku.  
  
    ```  
    Public Class windowsMessage  
        Private Declare Auto Function mb Lib "user32.dll" Alias "MessageBox" (  
            ByVal hWnd As Integer,   
            ByVal lpText As String,   
            ByVal lpCaption As String,   
            ByVal uType As UInteger) As Integer  
        Private Const MB_OK As UInteger = 0  
        Private Const MB_ICONEXCLAMATION As UInteger = &H30  
        Private Const IDOK As UInteger = 1  
        Private Const IDCLOSE As UInteger = 8  
        Private Const c As UInteger = MB_OK Or MB_ICONEXCLAMATION  
        Public Function messageThroughWindows() As String  
            Dim r As Integer = mb(0, "Click OK if you see this!",   
                "Windows API call", c)  
            Dim s As String = "Windows API MessageBox returned " &  
                 CStr(r)& vbCrLf & "(IDOK = " & CStr(IDOK) &  
                 ", IDCLOSE = " & CStr(IDCLOSE) & ")"  
            Return s  
        End Function  
    End Class  
    ```  
  
     Można przetestować funkcji `messageThroughWindows` następującym kodem.  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  `UInteger`, `ULong`, `UShort`, I `SByte` typy danych nie są częścią [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik który używa ich.  
  
    > [!IMPORTANT]
    >  Wywołania do kodu niezarządzanego, takich jak interfejsu programowania aplikacji (API), system Windows udostępnia kodu na potencjalne zagrożenia bezpieczeństwa.  
  
    > [!IMPORTANT]
    >  Wywołanie interfejsu API systemu Windows wymaga uprawnień kodu niezarządzanego, co może wpływać na jej wykonanie w sytuacjach częściowego zaufania. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.SecurityPermission> i [uprawnienia dostępu do kodu](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
