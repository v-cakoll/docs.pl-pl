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
ms.openlocfilehash: cbb66934833da2bd6f0b797944dbb9c4df267cfc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="7cf0b-102">Porady: usuwanie zasobu systemu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7cf0b-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="7cf0b-103">Można użyć `Using` bloku, aby zagwarantować, że system usuwa zasobu, gdy kod jest kończona bloku.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="7cf0b-104">Jest to przydatne, jeśli używasz zasób systemowy, który zużywa duże ilości pamięci lub innych składników również chcesz użyć.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="7cf0b-105">Po zakończeniu kodu z nim zlikwidować połączenia z bazą danych</span><span class="sxs-lookup"><span data-stu-id="7cf0b-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1.  <span data-ttu-id="7cf0b-106">Upewnij się, że możesz dołączyć odpowiednie [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient>).</span><span class="sxs-lookup"><span data-stu-id="7cf0b-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2.  <span data-ttu-id="7cf0b-107">Utwórz `Using` zablokować z `Using` i `End Using` instrukcje.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="7cf0b-108">Wewnątrz bloku umieść kod, który zajmuje się połączenie z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3.  <span data-ttu-id="7cf0b-109">Deklarowanie połączenia i Utwórz wystąpienie go jako część `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="7cf0b-110">Usuwa systemu zasobów, niezależnie od tego, jak zakończyć blok, w tym przypadku nieobsługiwany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="7cf0b-111">Należy pamiętać, że nie masz dostępu do `sqc` z poza `Using` zablokować, ponieważ jej zakres ogranicza się do bloku.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="7cf0b-112">Ten sam sposób można użyć w zasobach systemu, np. dojście do pliku lub otoki COM.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="7cf0b-113">Możesz użyć `Using` zablokować, jeśli chcesz mieć pewność opuścić zasobów dostępne dla innych składników po zostały zakończone `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="7cf0b-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7cf0b-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cf0b-114">See Also</span></span>  
 <xref:System.Data.SqlClient.SqlConnection>  
 [<span data-ttu-id="7cf0b-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="7cf0b-115">Control Flow</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/index.md)  
 [<span data-ttu-id="7cf0b-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="7cf0b-116">Decision Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/decision-structures.md)  
 [<span data-ttu-id="7cf0b-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="7cf0b-117">Loop Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/loop-structures.md)  
 [<span data-ttu-id="7cf0b-118">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="7cf0b-118">Other Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/other-control-structures.md)  
 [<span data-ttu-id="7cf0b-119">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="7cf0b-119">Nested Control Structures</span></span>](../../../../visual-basic/programming-guide/language-features/control-flow/nested-control-structures.md)  
 [<span data-ttu-id="7cf0b-120">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7cf0b-120">Using Statement</span></span>](../../../../visual-basic/language-reference/statements/using-statement.md)
