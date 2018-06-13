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
ms.openlocfilehash: afec9965c4ff728094e901eb4924ac94c432b300
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33643029"
---
# <a name="how-to-call-a-windows-function-that-takes-unsigned-types-visual-basic"></a><span data-ttu-id="beb50-102">Porady: wywoływanie funkcji Windows wykorzystującej typy bez znaku (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="beb50-102">How to: Call a Windows Function that Takes Unsigned Types (Visual Basic)</span></span>
<span data-ttu-id="beb50-103">Zużywają klasy, modułu lub struktury, która ma elementów członkowskich typu Liczba całkowita bez znaku, można uzyskać dostępu do tych elementów członkowskich za pomocą Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="beb50-103">If you are consuming a class, module, or structure that has members of unsigned integer types, you can access these members with Visual Basic.</span></span>  
  
### <a name="to-call-a-windows-function-that-takes-an-unsigned-type"></a><span data-ttu-id="beb50-104">Wywoływanie funkcji Windows wykorzystującej typu bez znaku</span><span class="sxs-lookup"><span data-stu-id="beb50-104">To call a Windows function that takes an unsigned type</span></span>  
  
1.  <span data-ttu-id="beb50-105">Użyj [instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) mówić Visual Basic biblioteki, który zawiera funkcję, jego nazwa jest w tej bibliotece jest jego sekwencja wywoływania i sposób konwertowania ciągów podczas wywoływania metody go.</span><span class="sxs-lookup"><span data-stu-id="beb50-105">Use a [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md) to tell Visual Basic which library holds the function, what its name is in that library, what its calling sequence is, and how to convert strings when calling it.</span></span>  
  
2.  <span data-ttu-id="beb50-106">W `Declare` instrukcji, użyj `UInteger`, `ULong`, `UShort`, lub `Byte` odpowiednio dla każdego parametru z typu bez znaku.</span><span class="sxs-lookup"><span data-stu-id="beb50-106">In the `Declare` statement, use `UInteger`, `ULong`, `UShort`, or `Byte` as appropriate for each parameter with an unsigned type.</span></span>  
  
3.  <span data-ttu-id="beb50-107">Zajrzyj do dokumentacji wywoływany można znaleźć nazwy i wartości stałe, który używa funkcji systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="beb50-107">Consult the documentation for the Windows function you are calling to find the names and values of the constants it uses.</span></span> <span data-ttu-id="beb50-108">Wiele z tych są zdefiniowane w pliku WinUser.h.</span><span class="sxs-lookup"><span data-stu-id="beb50-108">Many of these are defined in the WinUser.h file.</span></span>  
  
4.  <span data-ttu-id="beb50-109">Deklarowanie stałych niezbędne w kodzie.</span><span class="sxs-lookup"><span data-stu-id="beb50-109">Declare the necessary constants in your code.</span></span> <span data-ttu-id="beb50-110">Wiele stałe systemu Windows są wartościami typu unsigned 32-bitowe i należy je określić `As``UInteger`.</span><span class="sxs-lookup"><span data-stu-id="beb50-110">Many Windows constants are 32-bit unsigned values, and you should declare these `As``UInteger`.</span></span>  
  
5.  <span data-ttu-id="beb50-111">Wywołanie funkcji w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="beb50-111">Call the function in the normal way.</span></span> <span data-ttu-id="beb50-112">Poniższy przykład wywołuje funkcję Windows `MessageBox`, który przyjmuje argument liczby całkowitej bez znaku.</span><span class="sxs-lookup"><span data-stu-id="beb50-112">The following example calls the Windows function `MessageBox`, which takes an unsigned integer argument.</span></span>  
  
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
  
     <span data-ttu-id="beb50-113">Można przetestować funkcji `messageThroughWindows` następującym kodem.</span><span class="sxs-lookup"><span data-stu-id="beb50-113">You can test the function `messageThroughWindows` with the following code.</span></span>  
  
    ```  
    Public Sub consumeWindowsMessage()  
        Dim w As New windowsMessage  
        w.messageThroughWindows()  
    End Sub  
    ```  
  
    > [!CAUTION]
    >  <span data-ttu-id="beb50-114">`UInteger`, `ULong`, `UShort`, I `SByte` typy danych nie są częścią [niezależność od języka i elementy niezależne od języka](../../../standard/language-independence-and-language-independent-components.md) (ze specyfikacją CLS), więc kodu zgodne ze specyfikacją CLS nie może korzystać składnik który używa ich.</span><span class="sxs-lookup"><span data-stu-id="beb50-114">The `UInteger`, `ULong`, `UShort`, and `SByte` data types are not part of the [Language Independence and Language-Independent Components](../../../standard/language-independence-and-language-independent-components.md) (CLS), so CLS-compliant code cannot consume a component that uses them.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="beb50-115">Wywołania do kodu niezarządzanego, takich jak interfejsu programowania aplikacji (API), system Windows udostępnia kodu na potencjalne zagrożenia bezpieczeństwa.</span><span class="sxs-lookup"><span data-stu-id="beb50-115">Making a call to unmanaged code, such as the Windows application programming interface (API), exposes your code to potential security risks.</span></span>  
  
    > [!IMPORTANT]
    >  <span data-ttu-id="beb50-116">Wywołanie interfejsu API systemu Windows wymaga uprawnień kodu niezarządzanego, co może wpływać na jej wykonanie w sytuacjach częściowego zaufania.</span><span class="sxs-lookup"><span data-stu-id="beb50-116">Calling the Windows API requires unmanaged code permission, which might affect its execution in partial-trust situations.</span></span> <span data-ttu-id="beb50-117">Aby uzyskać więcej informacji, zobacz <xref:System.Security.Permissions.SecurityPermission> i [uprawnienia dostępu do kodu](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span><span class="sxs-lookup"><span data-stu-id="beb50-117">For more information, see <xref:System.Security.Permissions.SecurityPermission> and [Code Access Permissions](http://msdn.microsoft.com/library/e5ae402f-6dda-4732-bbe8-77296630f675).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="beb50-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="beb50-118">See Also</span></span>  
 [<span data-ttu-id="beb50-119">Typy danych</span><span class="sxs-lookup"><span data-stu-id="beb50-119">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="beb50-120">Integer, typ danych</span><span class="sxs-lookup"><span data-stu-id="beb50-120">Integer Data Type</span></span>](../../../visual-basic/language-reference/data-types/integer-data-type.md)  
 [<span data-ttu-id="beb50-121">UInteger, typ danych</span><span class="sxs-lookup"><span data-stu-id="beb50-121">UInteger Data Type</span></span>](../../../visual-basic/language-reference/data-types/uinteger-data-type.md)  
 [<span data-ttu-id="beb50-122">Declare, instrukcja</span><span class="sxs-lookup"><span data-stu-id="beb50-122">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
 [<span data-ttu-id="beb50-123">Przewodnik: wywoływanie interfejsów API systemu Windows</span><span class="sxs-lookup"><span data-stu-id="beb50-123">Walkthrough: Calling Windows APIs</span></span>](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)
