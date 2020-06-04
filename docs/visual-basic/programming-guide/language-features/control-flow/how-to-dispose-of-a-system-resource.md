---
title: 'Porady: usuwanie zasobu systemu'
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
ms.openlocfilehash: dd15c6746628f45b072d46eea40051ed9afb7921
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403501"
---
# <a name="how-to-dispose-of-a-system-resource-visual-basic"></a><span data-ttu-id="9fa72-102">Porady: usuwanie zasobu systemu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9fa72-102">How to: Dispose of a System Resource (Visual Basic)</span></span>
<span data-ttu-id="9fa72-103">Można użyć `Using` bloku, aby zagwarantować, że system usuwa zasób, gdy kod opuszcza blok.</span><span class="sxs-lookup"><span data-stu-id="9fa72-103">You can use a `Using` block to guarantee that the system disposes of a resource when your code exits the block.</span></span> <span data-ttu-id="9fa72-104">Jest to przydatne, jeśli używasz zasobu systemowego, który zużywa dużą ilość pamięci, lub że chcesz również użyć innych składników.</span><span class="sxs-lookup"><span data-stu-id="9fa72-104">This is useful if you are using a system resource that consumes a large amount of memory, or that other components also want to use.</span></span>  
  
### <a name="to-dispose-of-a-database-connection-when-your-code-is-finished-with-it"></a><span data-ttu-id="9fa72-105">Aby usunąć połączenie z bazą danych, gdy kod jest gotowy</span><span class="sxs-lookup"><span data-stu-id="9fa72-105">To dispose of a database connection when your code is finished with it</span></span>  
  
1. <span data-ttu-id="9fa72-106">Upewnij się, że dołączysz odpowiednią [instrukcję Imports (przestrzeń nazw i typ platformy .NET)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) dla połączenia z bazą danych na początku pliku źródłowego (w tym przypadku <xref:System.Data.SqlClient> ).</span><span class="sxs-lookup"><span data-stu-id="9fa72-106">Make sure you include the appropriate [Imports Statement (.NET Namespace and Type)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md) for the database connection at the beginning of your source file (in this case, <xref:System.Data.SqlClient>).</span></span>  
  
2. <span data-ttu-id="9fa72-107">Utwórz `Using` blok z `Using` `End Using` instrukcjami i.</span><span class="sxs-lookup"><span data-stu-id="9fa72-107">Create a `Using` block with the `Using` and `End Using` statements.</span></span> <span data-ttu-id="9fa72-108">W bloku należy umieścić kod, który zajmuje się połączeniem z bazą danych.</span><span class="sxs-lookup"><span data-stu-id="9fa72-108">Inside the block, put the code that deals with the database connection.</span></span>  
  
3. <span data-ttu-id="9fa72-109">Zadeklaruj połączenie i Utwórz wystąpienie go jako część `Using` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="9fa72-109">Declare the connection and create an instance of it as part of the `Using` statement.</span></span>  
  
    ```vb  
    ' Insert the following line at the beginning of your source file.  
    Imports System.Data.SqlClient  
    Public Sub AccessSql(ByVal s As String)  
        Using sqc As New System.Data.SqlClient.SqlConnection(s)  
            MsgBox("Connected with string """ & sqc.ConnectionString & """")  
        End Using  
    End Sub  
    ```  
  
     <span data-ttu-id="9fa72-110">System usuwa zasób niezależnie od tego, jak zamknięto blok, w tym przypadek nieobsłużonego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="9fa72-110">The system disposes of the resource no matter how you exit the block, including the case of an unhandled exception.</span></span>  
  
     <span data-ttu-id="9fa72-111">Należy zauważyć, że nie można uzyskać dostępu `sqc` spoza `Using` bloku, ponieważ jego zakres jest ograniczony do bloku.</span><span class="sxs-lookup"><span data-stu-id="9fa72-111">Note that you cannot access `sqc` from outside the `Using` block, because its scope is limited to the block.</span></span>  
  
     <span data-ttu-id="9fa72-112">Tej samej metody można użyć w odniesieniu do zasobu systemowego, takiego jak dojście do pliku lub otoka COM.</span><span class="sxs-lookup"><span data-stu-id="9fa72-112">You can use this same technique on a system resource such as a file handle or a COM wrapper.</span></span> <span data-ttu-id="9fa72-113">Możesz użyć `Using` bloku, gdy chcesz, aby pozostawić zasób dostępny dla innych składników po zakończeniu `Using` bloku.</span><span class="sxs-lookup"><span data-stu-id="9fa72-113">You use a `Using` block when you want to be sure to leave the resource available for other components after you have exited the `Using` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9fa72-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9fa72-114">See also</span></span>

- <xref:System.Data.SqlClient.SqlConnection>
- [<span data-ttu-id="9fa72-115">Przepływ sterowania</span><span class="sxs-lookup"><span data-stu-id="9fa72-115">Control Flow</span></span>](index.md)
- [<span data-ttu-id="9fa72-116">Struktury decyzji</span><span class="sxs-lookup"><span data-stu-id="9fa72-116">Decision Structures</span></span>](decision-structures.md)
- [<span data-ttu-id="9fa72-117">Struktury pętli</span><span class="sxs-lookup"><span data-stu-id="9fa72-117">Loop Structures</span></span>](loop-structures.md)
- [<span data-ttu-id="9fa72-118">Inne struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="9fa72-118">Other Control Structures</span></span>](other-control-structures.md)
- [<span data-ttu-id="9fa72-119">Zagnieżdżone struktury sterujące</span><span class="sxs-lookup"><span data-stu-id="9fa72-119">Nested Control Structures</span></span>](nested-control-structures.md)
- [<span data-ttu-id="9fa72-120">Using, instrukcja</span><span class="sxs-lookup"><span data-stu-id="9fa72-120">Using Statement</span></span>](../../../language-reference/statements/using-statement.md)
