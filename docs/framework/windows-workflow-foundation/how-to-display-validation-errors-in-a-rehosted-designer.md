---
title: "Porady: wyświetlanie błędów sprawdzania poprawności w Projektancie Rehosted"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: b9f76f1ad5282ecf10a3ce58db0f6e1bd8df1b4d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="7eb71-102">Porady: wyświetlanie błędów sprawdzania poprawności w Projektancie Rehosted</span><span class="sxs-lookup"><span data-stu-id="7eb71-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="7eb71-103">W tym temacie opisano sposób pobierania i opublikuj błędy sprawdzania poprawności w rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="7eb71-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="7eb71-104">To zapewnia procedury, aby upewnić się, że przepływ pracy w Projektancie rehosted jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="7eb71-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="7eb71-105">To zadanie ma dwie części.</span><span class="sxs-lookup"><span data-stu-id="7eb71-105">This task has two parts.</span></span> <span data-ttu-id="7eb71-106">Pierwsza to zapewniać implementację <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="7eb71-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="7eb71-107">Brak jednej metody krytyczne do zaimplementowania w tym interfejsie <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> który zostanie przekazany listę <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="7eb71-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="7eb71-108">Po implementującej interfejs, możesz pobrać informacje o błędzie publikując wystąpienia tej implementacji Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="7eb71-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="7eb71-109">Zaimplementuj interfejs IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="7eb71-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="7eb71-110">Oto przykład kodu dla prostych implementacji, która zapisze błędy sprawdzania poprawności w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="7eb71-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```  
    using System.Activities.Presentation.Validation;  
    using System.Collections.Generic;  
    using System.Diagnostics;  
    using System.Linq;  
  
    namespace VariableFinderShell  
    {  
        class DebugValidationErrorService : IValidationErrorService  
        {  
            public void ShowValidationErrors(IList<ValidationErrorInfo> errors)  
            {  
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="7eb71-111">Publikowanie w kontekście edycji</span><span class="sxs-lookup"><span data-stu-id="7eb71-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="7eb71-112">Oto kod, który będzie publikować to Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="7eb71-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
