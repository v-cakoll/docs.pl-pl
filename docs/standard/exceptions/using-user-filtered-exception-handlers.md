---
title: Używanie obsługi wyjątków filtrowanych przez użytkownika
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
author: mairaw
ms.author: mairaw
ms.openlocfilehash: d1e771a95542153dfad0981d3198e6b4c31cdeb9
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "45987750"
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="c66df-102">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c66df-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="c66df-103">Obecnie usługa Visual Basic obsługuje wyjątki filtrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c66df-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="c66df-104">Programy obsługi wyjątków filtrowanych przez użytkownika przechwytywać i obsługiwać wyjątki, na podstawie wymagań zdefiniowanych dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c66df-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="c66df-105">Użyj tych procedur obsługi **Catch** instrukcję, określając **podczas** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c66df-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="c66df-106">Ta technika jest przydatna, gdy obiekt określony wyjątek odpowiada wiele błędów.</span><span class="sxs-lookup"><span data-stu-id="c66df-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="c66df-107">W tym przypadku obiekt ma zazwyczaj właściwość, która zawiera kod błędu skojarzony z błędem.</span><span class="sxs-lookup"><span data-stu-id="c66df-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="c66df-108">Właściwości kodu błędu w wyrażeniu służy do wybierania tylko określony błąd mają być obsługiwane w tym **Catch** klauzuli.</span><span class="sxs-lookup"><span data-stu-id="c66df-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="c66df-109">W poniższym przykładzie w języku Visual Basic pokazano **Catch/gdy** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="c66df-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="c66df-110">Wyrażenie klauzuli filtrowanych przez użytkownika nie ma ograniczeń w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="c66df-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="c66df-111">Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowanych przez użytkownika, ten wyjątek jest odrzucana i wyrażenie filtru jest uznawany za zostały ocenione na wartość false.</span><span class="sxs-lookup"><span data-stu-id="c66df-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="c66df-112">W takim wypadku środowisko uruchomieniowe języka wspólnego kontynuuje wyszukiwanie obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="c66df-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="c66df-113">Łączenie określonego wyjątku i klauzule filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="c66df-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="c66df-114">Instrukcja catch może zawierać zarówno określony wyjątek, jak i klauzule filtrowanych przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c66df-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="c66df-115">Środowisko uruchomieniowe sprawdza określony wyjątek, najpierw.</span><span class="sxs-lookup"><span data-stu-id="c66df-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="c66df-116">Jeśli określony wyjątek zakończy się powodzeniem, środowisko uruchomieniowe wykonuje filtr użytkownika.</span><span class="sxs-lookup"><span data-stu-id="c66df-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="c66df-117">Filtr ogólny może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klasy.</span><span class="sxs-lookup"><span data-stu-id="c66df-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="c66df-118">Należy zauważyć kolejność klauzul dwóch filtru nie można cofnąć.</span><span class="sxs-lookup"><span data-stu-id="c66df-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="c66df-119">W poniższym przykładzie w języku Visual Basic przedstawia określony wyjątek `ClassLoadException` w **Catch** instrukcji, a także przy użyciu klauzuli filtrowanych przez użytkownika **podczas** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="c66df-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="c66df-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c66df-120">See also</span></span>

- [<span data-ttu-id="c66df-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="c66df-121">Exceptions</span></span>](index.md)
