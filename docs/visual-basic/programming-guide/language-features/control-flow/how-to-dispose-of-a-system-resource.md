---
title: 'Instrukcje: Usuwanie zasobu systemu (Visual Basic)'
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
ms.openlocfilehash: 798650bbefc0c5b2ac097b87ab44a2b380117939
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54523223"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="c1d1d-102">Instrukcje: Usuwanie zasobu systemu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c1d1d-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="c1d1d-103">Możesz użyć `Using` bloku, aby zagwarantować, że system Usuwa zasób po kodzie zamyka blok.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="c1d1d-104">Jest to przydatne, jeśli używasz zasób systemowy, który używa dużej ilości pamięci, lub też używać innych składników.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="c1d1d-105">Aby usunąć połączenie z bazą danych po zakończeniu swój kod z nim</span><span class="sxs-lookup"><span data-stu-id="c1d1d-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="c1d1d-106">Upewnij się, możesz dołączyć odpowiednie [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="c1d1d-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="c1d1d-107">Tworzenie `Using` blokowania z `Using` i `End Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="c1d1d-108">Wewnątrz bloku umieść kod, który zajmuje się połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="c1d1d-109">Deklarowanie połączenie i utworzyć jej wystąpienie w ramach `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="c1d1d-110">Usuwa system zasobów, niezależnie od tego, jak zamknąć blok, w tym przypadku Wystąpił nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="c1d1d-111">Należy zauważyć, że nie masz dostępu do `sqc` z poza `Using` zablokować, ponieważ jej zakres jest ograniczony do bloku.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="c1d1d-112">Można użyć tej samej techniki, w zasobach systemu, takie jak dojście do pliku lub otoka COM.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="c1d1d-113">Możesz użyć `Using` zablokować, jeśli chcesz mieć pewność, że opuścić zasób jest dostępny dla innych składników po zostały zakończone `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="c1d1d-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c1d1d-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c1d1d-114">See also</span></span>
- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="c1d1d-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="c1d1d-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)
- [<span data-ttu-id="c1d1d-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="c1d1d-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)
- [<span data-ttu-id="c1d1d-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="c1d1d-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)
- [<span data-ttu-id="c1d1d-118">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="c1d1d-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)
- [<span data-ttu-id="c1d1d-119">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="c1d1d-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)
- [<span data-ttu-id="c1d1d-120">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="c1d1d-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
