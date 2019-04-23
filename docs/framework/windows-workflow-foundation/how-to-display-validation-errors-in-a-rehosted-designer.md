---
title: 'Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59770909"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="2f0f5-102">Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie</span><span class="sxs-lookup"><span data-stu-id="2f0f5-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="2f0f5-103">W tym temacie opisano sposób pobierania i publikowanie błędów walidacji w rehostowanym [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2f0f5-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="2f0f5-104">Zapewnia to nam za pomocą procedury, aby upewnić się, że w rehostowanym projektancie przepływu pracy jest nieprawidłowa.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="2f0f5-105">To zadanie ma dwie części.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-105">This task has two parts.</span></span> <span data-ttu-id="2f0f5-106">Pierwszy jest zapewnienie implementację <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="2f0f5-107">Brak jednej metody krytycznej do zaimplementowania w tym interfejsie <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> który zostanie przekazany listę <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="2f0f5-108">Po zaimplementowaniu interfejsu, możesz pobrać informacje o błędzie, publikując wystąpienie tę implementację Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="2f0f5-109">Implementuj interfejs IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="2f0f5-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="2f0f5-110">Poniżej przedstawiono przykładowy kod dla prostych implementacji, który będzie zapisywał się błędy sprawdzania poprawności w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="2f0f5-111">Publikowanie Kontekst edycyjny</span><span class="sxs-lookup"><span data-stu-id="2f0f5-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="2f0f5-112">Poniżej przedstawiono kod, który będzie publikować to Kontekst edycyjny.</span><span class="sxs-lookup"><span data-stu-id="2f0f5-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
