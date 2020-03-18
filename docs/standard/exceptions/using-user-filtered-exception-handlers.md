---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "75708456"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="2cca4-102">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="2cca4-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="2cca4-103">Obecnie program Visual Basic obsługuje wyjątki filtrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2cca4-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="2cca4-104">Programy obsługi wyjątków filtrowane przez użytkownika przechwycają i obsługują wyjątki na podstawie wymagań zdefiniowanych dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cca4-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="2cca4-105">Te programy obsługi używać **Catch** instrukcji z **When** słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="2cca4-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="2cca4-106">Ta technika jest przydatna, gdy obiekt określonego wyjątku odpowiada wielu błędom.</span><span class="sxs-lookup"><span data-stu-id="2cca4-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="2cca4-107">W takim przypadku obiekt zazwyczaj ma właściwość, która zawiera kod błędu określonego skojarzonego z błędem.</span><span class="sxs-lookup"><span data-stu-id="2cca4-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="2cca4-108">Można użyć właściwości kodu błędu w wyrażeniu, aby wybrać tylko określony błąd, który ma być obsługiwany w tej **catch** klauzuli.</span><span class="sxs-lookup"><span data-stu-id="2cca4-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="2cca4-109">Poniższy przykład języka Visual Basic ilustruje **Catch/When** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="2cca4-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="2cca4-110">Wyrażenie klauzuli filtrowane przez użytkownika nie jest w żaden sposób ograniczone.</span><span class="sxs-lookup"><span data-stu-id="2cca4-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="2cca4-111">Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowanego przez użytkownika, ten wyjątek jest odrzucany, a wyrażenie filtru jest uważane za ocenione jako false.</span><span class="sxs-lookup"><span data-stu-id="2cca4-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="2cca4-112">W takim przypadku czas uruchomieniowy języka wspólnego kontynuuje wyszukiwanie obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="2cca4-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="2cca4-113">Łączenie wyjątku specyficznego i klauzul filtrowanych przez użytkowników</span><span class="sxs-lookup"><span data-stu-id="2cca4-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="2cca4-114">Catch Instrukcji może zawierać zarówno określonego wyjątku i klauzulfiltrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2cca4-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="2cca4-115">W czasie wykonywania testów określonego wyjątku pierwszy.</span><span class="sxs-lookup"><span data-stu-id="2cca4-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="2cca4-116">Jeśli określony wyjątek powiedzie się, środowisko uruchomieniowe wykonuje filtr użytkownika.</span><span class="sxs-lookup"><span data-stu-id="2cca4-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="2cca4-117">Filtr ogólny może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klasy.</span><span class="sxs-lookup"><span data-stu-id="2cca4-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="2cca4-118">Należy zauważyć, że kolejność dwóch klauzul filtru nie można odwrócić.</span><span class="sxs-lookup"><span data-stu-id="2cca4-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="2cca4-119">W poniższym przykładzie języka `ClassLoadException` Visual Basic przedstawiono określony wyjątek w **Catch** instrukcji, a także klauzuli filtrowane przez użytkownika przy użyciu **When** słowa kluczowego.</span><span class="sxs-lookup"><span data-stu-id="2cca4-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="2cca4-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2cca4-120">See also</span></span>

- [<span data-ttu-id="2cca4-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="2cca4-121">Exceptions</span></span>](index.md)
