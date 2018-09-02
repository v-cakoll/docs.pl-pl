---
title: 'Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)'
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
ms.openlocfilehash: d66b74f06abe6b337c24859c444f7a8c2aa52c13
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421526"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="3b760-102">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3b760-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="3b760-103">Używanym klasy, modułu lub struktura, która ma składowych typu Liczba całkowita bez znaku, można uzyskać dostęp do tych członków, za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="3b760-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="3b760-104">Aby wywołać funkcję Windows, która przyjmuje typ bez znaku</span><span class="sxs-lookup"><span data-stu-id="3b760-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="3b760-105">Użyj [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) mówić języka Visual Basic, biblioteki, która zawiera funkcję, jego nazwa jest w tej bibliotece, co to jest jego sekwencja wywoływania i sposób konwertowania ciągów przy wywoływaniu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="3b760-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="3b760-106">W `Declare` instrukcji, użyj `UInteger`, `ULong`, `UShort`, lub `Byte` odpowiednio dla każdego parametru za pomocą typ bez znaku.</span><span class="sxs-lookup"><span data-stu-id="3b760-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="3b760-107">Zajrzyj do dokumentacji dla funkcji Windows, wywoływany można znaleźć nazwy i wartości stałe, które są używane.</span><span class="sxs-lookup"><span data-stu-id="3b760-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="3b760-108">Wiele z nich są zdefiniowane w pliku WinUser.h.</span><span class="sxs-lookup"><span data-stu-id="3b760-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="3b760-109">Deklarowanie stałych niezbędne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="3b760-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="3b760-110">Wiele stałe Windows są wartości bez znaku 32-bitowe i należy je zadeklarować `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="3b760-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="3b760-111">Wywołaj funkcję w normalny sposób.</span><span class="sxs-lookup"><span data-stu-id="3b760-111">Call the function in the normal way.</span></span> <span data-ttu-id="3b760-112">Poniższy przykład wywołuje funkcję Windows `MessageBox`, który przyjmuje argument typu Liczba całkowita bez znaku.</span><span class="sxs-lookup"><span data-stu-id="3b760-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="3b760-113">Możesz przetestować funkcję `messageThroughWindows` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="3b760-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="3b760-114">`UInteger`, `ULong`, `UShort`, I `SByte` typy danych nie są częścią [niezależność od języka i składniki niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (CLS), więc kodu zgodne ze specyfikacją CLS nie może używać składnika, są one używane.</span><span class="sxs-lookup"><span data-stu-id="3b760-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3b760-115">Wywołania do kodu niezarządzanego, takich jak interfejsu programowania aplikacji (API), Windows udostępnia kod na potencjalne zagrożenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="3b760-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="3b760-116">Wywołanie interfejsu API Windows wymaga uprawnienie niezarządzanego kodu, które mogą mieć wpływ na jej wykonanie w sytuacjach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="3b760-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="3b760-117">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.SecurityPermission> i [uprawnienia dostępu kodu](https://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span><span class="sxs-lookup"><span data-stu-id="3b760-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](https://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b760-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b760-118">See Also</span></span>  
 [<span data-ttu-id="3b760-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="3b760-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)  
 [<span data-ttu-id="3b760-120">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="3b760-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="3b760-121">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="3b760-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="3b760-122">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3b760-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="3b760-123">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="3b760-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
