---
title: 'Porady: wyświetlanie błędów sprawdzania poprawności w Projektancie Rehosted'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 8f70b190042d167741bbadc4e1645756fe5b830d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33512570"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="9cdf0-102">Porady: wyświetlanie błędów sprawdzania poprawności w Projektancie Rehosted</span><span class="sxs-lookup"><span data-stu-id="9cdf0-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="9cdf0-103">W tym temacie opisano sposób pobierania i opublikuj błędy sprawdzania poprawności w rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9cdf0-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="9cdf0-104">To zapewnia procedury, aby upewnić się, że przepływ pracy w Projektancie rehosted jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="9cdf0-105">To zadanie ma dwie części.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-105">This task has two parts.</span></span> <span data-ttu-id="9cdf0-106">Pierwsza to zapewniać implementację <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="9cdf0-107">Brak jednej metody krytyczne do zaimplementowania w tym interfejsie <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> który zostanie przekazany listę <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="9cdf0-108">Po implementującej interfejs, możesz pobrać informacje o błędzie publikując wystąpienia tej implementacji Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="9cdf0-109">Zaimplementuj interfejs IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="9cdf0-109">Implement the IValidationErrorService Interface</span></span>  
  
1.  <span data-ttu-id="9cdf0-110">Oto przykład kodu dla prostych implementacji, która zapisze błędy sprawdzania poprawności w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="9cdf0-111">Publikowanie w kontekście edycji</span><span class="sxs-lookup"><span data-stu-id="9cdf0-111">Publishing to the Editing Context</span></span>  
  
1.  <span data-ttu-id="9cdf0-112">Oto kod, który będzie publikować to Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="9cdf0-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
