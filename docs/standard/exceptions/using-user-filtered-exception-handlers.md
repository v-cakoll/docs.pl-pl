---
title: "Używanie obsługi wyjątków filtrowanych przez użytkownika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="using-user-filtered-exception-handlers"></a><span data-ttu-id="e1029-102">Używanie obsługi wyjątków filtrowanych przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e1029-102">Using User-Filtered Exception Handlers</span></span>
<span data-ttu-id="e1029-103">Visual Basic obsługuje obecnie wyjątki filtrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1029-103">Currently, Visual Basic supports user-filtered exceptions.</span></span> <span data-ttu-id="e1029-104">Programy obsługi wyjątków filtrowanych przez użytkownika wychwycić i obsłużyć wyjątków na podstawie wymagań zdefiniowanych dla wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e1029-104">User-filtered exception handlers catch and handle exceptions based on requirements you define for the exception.</span></span> <span data-ttu-id="e1029-105">Użyj tych programów obsługi **Catch** instrukcji z **podczas** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e1029-105">These handlers use the **Catch** statement with the **When** keyword.</span></span>  
  
 <span data-ttu-id="e1029-106">Ta technika jest przydatna, gdy obiekt określonego wyjątku odpowiada wiele błędów.</span><span class="sxs-lookup"><span data-stu-id="e1029-106">This technique is useful when a particular exception object corresponds to multiple errors.</span></span> <span data-ttu-id="e1029-107">W takim przypadku obiekt zwykle ma właściwość, która zawiera kod błędu skojarzony z powodu błędu.</span><span class="sxs-lookup"><span data-stu-id="e1029-107">In this case, the object typically has a property that contains the specific error code associated with the error.</span></span> <span data-ttu-id="e1029-108">Aby wybrać tylko określony błąd mają być obsługiwane w tym służy właściwości kodu błędu w wyrażeniu **Catch** klauzuli.</span><span class="sxs-lookup"><span data-stu-id="e1029-108">You can use the error code property in the expression to select only the particular error you want to handle in that **Catch** clause.</span></span>  
  
 <span data-ttu-id="e1029-109">Przedstawiono w poniższym przykładzie w języku Visual Basic **wystąpienia Catch** instrukcji.</span><span class="sxs-lookup"><span data-stu-id="e1029-109">The following Visual Basic example illustrates the **Catch/When** statement.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 <span data-ttu-id="e1029-110">Wyrażenie klauzuli filtrowane przez użytkownika nie jest ograniczona w dowolny sposób.</span><span class="sxs-lookup"><span data-stu-id="e1029-110">The expression of the user-filtered clause is not restricted in any way.</span></span> <span data-ttu-id="e1029-111">Jeśli wystąpi wyjątek podczas wykonywania wyrażenia filtrowane przez użytkownika, ten wyjątek jest odrzucany i wyrażenie filtru jest uznawany za obliczenia ma wartość false.</span><span class="sxs-lookup"><span data-stu-id="e1029-111">If an exception occurs during execution of the user-filtered expression, that exception is discarded and the filter expression is considered to have evaluated to false.</span></span> <span data-ttu-id="e1029-112">W takim przypadku środowisko uruchomieniowe języka wspólnego kontynuuje wyszukiwanie programu obsługi dla bieżącego wyjątku.</span><span class="sxs-lookup"><span data-stu-id="e1029-112">In this case, the common language runtime continues the search for a handler for the current exception.</span></span>  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a><span data-ttu-id="e1029-113">Łączenie określonego wyjątku i klauzule filtrowane przez użytkownika</span><span class="sxs-lookup"><span data-stu-id="e1029-113">Combining the Specific Exception and the User-Filtered Clauses</span></span>  
 <span data-ttu-id="e1029-114">Instrukcji catch może zawierać zarówno określony wyjątek, jak i klauzule filtrowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="e1029-114">A catch statement can contain both the specific exception and the user-filtered clauses.</span></span> <span data-ttu-id="e1029-115">Środowisko uruchomieniowe testów najpierw określony wyjątek.</span><span class="sxs-lookup"><span data-stu-id="e1029-115">The runtime tests the specific exception first.</span></span> <span data-ttu-id="e1029-116">Jeśli określony wyjątek zakończy się powodzeniem, środowisko uruchomieniowe wykonuje filtr użytkowników.</span><span class="sxs-lookup"><span data-stu-id="e1029-116">If the specific exception succeeds, the runtime executes the user filter.</span></span> <span data-ttu-id="e1029-117">Ogólne filtru może zawierać odwołanie do zmiennej zadeklarowanej w filtrze klasy.</span><span class="sxs-lookup"><span data-stu-id="e1029-117">The generic filter can contain a reference to the variable declared in the class filter.</span></span> <span data-ttu-id="e1029-118">Należy pamiętać, kolejność klauzul dwóch filtru nie można cofnąć.</span><span class="sxs-lookup"><span data-stu-id="e1029-118">Note that the order of the two filter clauses cannot be reversed.</span></span>  
  
 <span data-ttu-id="e1029-119">W poniższym przykładzie w języku Visual Basic zawiera określony wyjątek `ClassLoadException` w **Catch** instrukcji, a także za pomocą klauzuli filtrowane przez użytkownika **podczas** — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="e1029-119">The following Visual Basic example shows the specific exception `ClassLoadException` in the **Catch** statement as well as the user-filtered clause using the **When** keyword.</span></span>  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a><span data-ttu-id="e1029-120">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e1029-120">See Also</span></span>
[<span data-ttu-id="e1029-121">Wyjątki</span><span class="sxs-lookup"><span data-stu-id="e1029-121">Exceptions</span></span>](index.md)
