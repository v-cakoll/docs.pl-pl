---
title: 'Porady: usuwanie zasobu systemu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- Using statement [Visual Basic], disposing of system resources
- Visual Basic code, control flow
- system resources, disposing of
- resources [Visual Basic], disposing of system
- system resources
- Using statement [Visual Basic], Using...End Using
- Using block
ms.assetid: 8be2b239-8090-419b-8e7e-bcaa75b0ecc8
ms.openlocfilehash: c780ee1a174ad044593960bc30a3ee2e1f929390
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72583145"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="47441-102">Porady: usuwanie zasobu systemu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="47441-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="47441-103">Można użyć bloku `Using`, aby zagwarantować, że system usuwa zasób, gdy kod opuszcza blok.</span><span class="sxs-lookup"><span data-stu-id="47441-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="47441-104">Jest to przydatne, jeśli używasz zasobu systemowego, który zużywa dużą ilość pamięci, lub że chcesz również użyć innych składników.</span><span class="sxs-lookup"><span data-stu-id="47441-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="47441-105">Aby usunąć połączenie z bazą danych, gdy kod jest gotowy</span><span class="sxs-lookup"><span data-stu-id="47441-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="47441-106">Upewnij się, że dołączysz odpowiednią [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="47441-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="47441-107">Utwórz blok `Using` przy użyciu instrukcji `Using` i `End Using`.</span><span class="sxs-lookup"><span data-stu-id="47441-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="47441-108">W bloku należy umieścić kod, który zajmuje się połączeniem z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="47441-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="47441-109">Zadeklaruj połączenie i Utwórz wystąpienie go jako część instrukcji `Using`.</span><span class="sxs-lookup"><span data-stu-id="47441-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="47441-110">System usuwa zasób niezależnie od tego, jak zamknięto blok, w tym przypadek nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="47441-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="47441-111">Należy zauważyć, że nie można uzyskać dostępu `sqc` spoza bloku `Using`, ponieważ jego zakres jest ograniczony do bloku.</span><span class="sxs-lookup"><span data-stu-id="47441-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="47441-112">Tej samej metody można użyć w odniesieniu do zasobu systemowego, takiego jak dojście do pliku lub otoka COM.</span><span class="sxs-lookup"><span data-stu-id="47441-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="47441-113">Blok `Using` jest używany, gdy chcesz, aby pozostawić zasób dostępny dla innych składników po zakończeniu bloku `Using`.</span><span class="sxs-lookup"><span data-stu-id="47441-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47441-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="47441-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="47441-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="47441-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="47441-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="47441-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="47441-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="47441-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="47441-118">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="47441-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="47441-119">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="47441-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="47441-120">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="47441-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
