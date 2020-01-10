---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
ms.openlocfilehash: 5537404178b746310f720c5b0c075c77287dda4c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75708456"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="cdf56-102">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="cdf56-102">Using User-Filtered Exception Handlers</span></span>

<span data-ttu-id="cdf56-103">Obecnie Visual Basic obsługuje wyjątki filtrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cdf56-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="cdf56-104">Programy obsługi wyjątków filtrowane przez użytkownika przechwytują i obsługują wyjątki na podstawie wymagań zdefiniowanych dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cdf56-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="cdf56-105">Te programy obsługi używają instrukcji **catch** z słowem kluczowym **when** .</span><span class="sxs-lookup"><span data-stu-id="cdf56-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="cdf56-106">Ta technika jest przydatna, gdy określony obiekt wyjątku odnosi się do wielu błędów.</span><span class="sxs-lookup"><span data-stu-id="cdf56-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="cdf56-107">W takim przypadku obiekt ma zazwyczaj właściwość, która zawiera konkretny kod błędu skojarzony z błędem.</span><span class="sxs-lookup"><span data-stu-id="cdf56-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="cdf56-108">Możesz użyć właściwości kod błędu w wyrażeniu, aby wybrać tylko konkretny błąd, który chcesz obsłużyć w tej klauzuli **catch** .</span><span class="sxs-lookup"><span data-stu-id="cdf56-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="cdf56-109">Poniższy przykład Visual Basic ilustruje instrukcję **catch/when** .</span><span class="sxs-lookup"><span data-stu-id="cdf56-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```vb
Try  
    'Try statements.  
    Catch When Err = VBErr_ClassLoadException
    'Catch statements.
End Try  
```  
  
 <span data-ttu-id="cdf56-110">Wyrażenie filtrowanej przez użytkownika klauzuli nie jest w żaden sposób ograniczone.</span><span class="sxs-lookup"><span data-stu-id="cdf56-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="cdf56-111">Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowanego przez użytkownika, ten wyjątek zostanie odrzucony i wyrażenie filtru jest uważane za szacowane na wartość false.</span><span class="sxs-lookup"><span data-stu-id="cdf56-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="cdf56-112">W takim przypadku środowisko uruchomieniowe języka wspólnego kontynuuje wyszukiwanie programu obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="cdf56-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="cdf56-113">Połączenie określonego wyjątku i klauzul filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="cdf56-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="cdf56-114">Instrukcja catch może zawierać zarówno określony wyjątek, jak i przefiltrowane przez użytkownika klauzule.</span><span class="sxs-lookup"><span data-stu-id="cdf56-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="cdf56-115">Środowisko uruchomieniowe najpierw sprawdza konkretny wyjątek.</span><span class="sxs-lookup"><span data-stu-id="cdf56-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="cdf56-116">Jeśli konkretny wyjątek się powiedzie, środowisko uruchomieniowe wykonuje filtr użytkownika.</span><span class="sxs-lookup"><span data-stu-id="cdf56-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="cdf56-117">Filtr generyczny może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klas.</span><span class="sxs-lookup"><span data-stu-id="cdf56-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="cdf56-118">Należy zauważyć, że nie można odwrócić kolejności dwóch klauzul filtru.</span><span class="sxs-lookup"><span data-stu-id="cdf56-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="cdf56-119">Poniższy przykład Visual Basic ilustruje konkretny wyjątek `ClassLoadException` w instrukcji **catch** , a także klauzulę filtrowana przez użytkownika przy użyciu słowa kluczowego **when** .</span><span class="sxs-lookup"><span data-stu-id="cdf56-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```vb
Try  
    'Try statements.
    Catch cle As ClassLoadException When cle.IsRecoverable()  
    'Catch statements.
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="cdf56-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cdf56-120">See also</span></span>

- [<span data-ttu-id="cdf56-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="cdf56-121">Exceptions</span></span>](index.md)
