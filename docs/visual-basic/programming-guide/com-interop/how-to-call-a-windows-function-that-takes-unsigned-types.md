---
title: 'Instrukcje: Wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: d1a679242f89c17e58a837ac2d356e1594972fb3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374560"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a>Instrukcje: Wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)

Używanym klasy, modułu lub struktura, która ma składowych typu Liczba całkowita bez znaku, można uzyskać dostęp do tych członków, za pomocą Visual Basic.

### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a>Aby wywołać funkcję Windows, która przyjmuje typ bez znaku

1. Użyj [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) mówić języka Visual Basic, biblioteki, która zawiera funkcję, jego nazwa jest w tej bibliotece, co to jest jego sekwencja wywoływania i sposób konwertowania ciągów przy wywoływaniu tego elementu.

2. W `Declare` instrukcji, użyj `UInteger`, `ULong`, `UShort`, lub `Byte` odpowiednio dla każdego parametru za pomocą typ bez znaku.

3. Zajrzyj do dokumentacji dla funkcji Windows, wywoływany można znaleźć nazwy i wartości stałe, które są używane. Wiele z nich są zdefiniowane w pliku WinUser.h.

4. Deklarowanie stałych niezbędne w kodzie. Wiele stałe Windows są wartości bez znaku 32-bitowe i należy je zadeklarować `As UInteger`.

5. Wywołaj funkcję w normalny sposób. Poniższy przykład wywołuje funkcję Windows `MessageBox`, który przyjmuje argument typu Liczba całkowita bez znaku.

    ```vb
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

     Możesz przetestować funkcję `messageThroughWindows` następującym kodem.

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > `UInteger`, `ULong`, `UShort`, I `SByte` typy danych nie są częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), więc kodu zgodne ze specyfikacją CLS nie może używać składnika, są one używane.

    > [!IMPORTANT]
    > Wywołania do kodu niezarządzanego, takich jak interfejsu programowania aplikacji (API), Windows udostępnia kod na potencjalne zagrożenia bezpieczeństwa.

    > [!IMPORTANT]
    > Wywołanie interfejsu API Windows wymaga uprawnienie niezarządzanego kodu, które mogą mieć wpływ na jej wykonanie w sytuacjach częściowego zaufania. Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.SecurityPermission> i [uprawnienia dostępu kodu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).

## <a name="see-also"></a>Zobacz także

- [Typy danych](../../../visual-basic/language-reference/data-types/index.md)
- [Integer, typ danych](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [UInteger, typ danych](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)
- [Przewodnik: wywoływanie interfejsów API systemu Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
