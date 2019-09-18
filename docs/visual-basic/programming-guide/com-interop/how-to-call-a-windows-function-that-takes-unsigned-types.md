---
title: 'Instrukcje: Wywołaj funkcję systemu Windows, która pobiera typy bez znaku (Visual Basic)'
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
ms.openlocfilehash: 97075fb6149ed8c0ce06318d0e5bb6f01b841f30
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053326"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="a489b-102">Instrukcje: Wywołaj funkcję systemu Windows, która pobiera typy bez znaku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a489b-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>

<span data-ttu-id="a489b-103">Jeśli korzystasz z klasy, modułu lub struktury, która ma elementy członkowskie z niepodpisanymi typami całkowitymi, możesz uzyskać dostęp do tych elementów członkowskich za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a489b-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>

## <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="a489b-104">Aby wywołać funkcję systemu Windows, która ma typ bez znaku</span><span class="sxs-lookup"><span data-stu-id="a489b-104">To call a Windows function that takes an unsigned type</span></span>

1. <span data-ttu-id="a489b-105">Użyj [instrukcji DECLARE](../../../visual-basic/language-reference/statements/declare-statement.md) , aby poinformować Visual Basic bibliotekę, w której znajduje się ta funkcja, jak jej nazwa znajduje się w tej bibliotece, co to jest sekwencja wywoływania i jak konwertować ciągi podczas wywoływania.</span><span class="sxs-lookup"><span data-stu-id="a489b-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>

2. <span data-ttu-id="a489b-106">`UInteger`W instrukcji Użyj ,`ULong` ,`UShort`, lub`Byte` , w zależności od parametru z niepodpisanym typem. `Declare`</span><span class="sxs-lookup"><span data-stu-id="a489b-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>

3. <span data-ttu-id="a489b-107">Zapoznaj się z dokumentacją funkcji systemu Windows, która jest wywoływana, aby znaleźć nazwy i wartości stałych, z których korzysta.</span><span class="sxs-lookup"><span data-stu-id="a489b-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="a489b-108">Wiele z nich jest zdefiniowanych w pliku WinUser. h.</span><span class="sxs-lookup"><span data-stu-id="a489b-108">Many of these are defined in the WinUser.h file.</span></span>

4. <span data-ttu-id="a489b-109">Zadeklaruj niezbędne stałe w kodzie.</span><span class="sxs-lookup"><span data-stu-id="a489b-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="a489b-110">Wiele stałych systemu Windows to 32-bitowe wartości bez znaku i należy je `As UInteger`zadeklarować.</span><span class="sxs-lookup"><span data-stu-id="a489b-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As UInteger`.</span></span>

5. <span data-ttu-id="a489b-111">Wywołaj funkcję w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="a489b-111">Call the function in the normal way.</span></span> <span data-ttu-id="a489b-112">Poniższy przykład wywołuje funkcję `MessageBox`systemu Windows, która przyjmuje argument liczby całkowitej bez znaku.</span><span class="sxs-lookup"><span data-stu-id="a489b-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>

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

     <span data-ttu-id="a489b-113">Funkcję `messageThroughWindows` można przetestować przy użyciu następującego kodu.</span><span class="sxs-lookup"><span data-stu-id="a489b-113">You can test the function `messageThroughWindows` with the following code.</span></span>

    ```vb
    Public Sub consumeWindowsMessage()
        Dim w As New windowsMessage
        w.messageThroughWindows()
    End Sub
    ```

    > [!CAUTION]
    > <span data-ttu-id="a489b-114">`UInteger` ,`ULong`, ,I`SByte` typy danych nie są częścią [niezależności od języka i składników niezależnych od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), więc kod zgodny ze specyfikacją CLS nie może zużywać składnika, który z nich korzysta. `UShort`</span><span class="sxs-lookup"><span data-stu-id="a489b-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a489b-115">Wywoływanie kodu niezarządzanego, takiego jak interfejs programowania aplikacji (API) systemu Windows, uwidacznia swój kod na potencjalne zagrożenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="a489b-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>

    > [!IMPORTANT]
    > <span data-ttu-id="a489b-116">Wywołanie interfejsu API systemu Windows wymaga uprawnień do kodu niezarządzanego, co może mieć wpływ na wykonywanie w sytuacjach częściowej relacji zaufania.</span><span class="sxs-lookup"><span data-stu-id="a489b-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="a489b-117">Aby uzyskać więcej informacji, <xref:System.Security.Permissions.SecurityPermission> Zobacz i [uprawnienia dostępu kodu](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span><span class="sxs-lookup"><span data-stu-id="a489b-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/h846e9b3(v=vs.100)).</span></span>

## <a name="see-also"></a><span data-ttu-id="a489b-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a489b-118">See also</span></span>

- [<span data-ttu-id="a489b-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="a489b-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="a489b-120">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="a489b-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)
- [<span data-ttu-id="a489b-121">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="a489b-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)
- [<span data-ttu-id="a489b-122">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a489b-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)
- [<span data-ttu-id="a489b-123">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="a489b-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
