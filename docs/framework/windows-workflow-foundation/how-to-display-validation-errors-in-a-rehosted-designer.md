---
title: 'Instrukcje: wyświetlanie błędów walidacji w rehostowanym projektancie'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: bd0c2c10665de4bc3364938167101655a9bdd056
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/03/2019
ms.locfileid: "74716283"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="f7eb9-102">Instrukcje: wyświetlanie błędów walidacji w rehostowanym projektancie</span><span class="sxs-lookup"><span data-stu-id="f7eb9-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="f7eb9-103">W tym temacie opisano sposób pobierania i publikowania błędów walidacji w przeszukiwanym Projektant przepływu pracy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-103">This topic describes how to retrieve and publish validation errors in a rehosted Windows Workflow Designer.</span></span> <span data-ttu-id="f7eb9-104">Dzięki temu można sprawdzić, czy przepływ pracy w przewidzianym przez niego projektancie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="f7eb9-105">To zadanie ma dwie części.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-105">This task has two parts.</span></span> <span data-ttu-id="f7eb9-106">Pierwszym etapem jest dostarczenie <xref:System.Activities.Presentation.Validation.IValidationErrorService>implementacji.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="f7eb9-107">Istnieje jedna metoda krytyczna do zaimplementowania w tym interfejsie, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> co spowoduje przekazanie listy <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach do dziennika debugowania.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="f7eb9-108">Po wdrożeniu interfejsu można pobrać informacje o błędzie, publikując wystąpienie tej implementacji w kontekście edycji.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="f7eb9-109">Implementowanie interfejsu IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="f7eb9-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="f7eb9-110">Oto przykład kodu dla prostej implementacji, która będzie zapisywać błędy walidacji w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
    ```csharp  
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
                errors.ToList().ForEach(vei => Debug.WriteLine($"Error: {vei.Message}"));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="f7eb9-111">Publikowanie w kontekście edycji</span><span class="sxs-lookup"><span data-stu-id="f7eb9-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="f7eb9-112">Oto kod, który zostanie opublikowany w kontekście edycji.</span><span class="sxs-lookup"><span data-stu-id="f7eb9-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
