---
title: 'Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: 608868882f4bec23c03f0ec78f65673e76056030
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989662"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a><span data-ttu-id="d226e-102">Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie</span><span class="sxs-lookup"><span data-stu-id="d226e-102">How to: Display Validation Errors in a Rehosted Designer</span></span>
<span data-ttu-id="d226e-103">W tym temacie opisano sposób pobierania i publikowania błędów walidacji w rehostie [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d226e-103">This topic describes how to retrieve and publish validation errors in a rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)].</span></span> <span data-ttu-id="d226e-104">Dzięki temu można sprawdzić, czy przepływ pracy w przewidzianym przez niego projektancie jest prawidłowy.</span><span class="sxs-lookup"><span data-stu-id="d226e-104">This provides us with a procedure to confirm that a workflow in a rehosted designer is valid.</span></span>  
  
 <span data-ttu-id="d226e-105">To zadanie ma dwie części.</span><span class="sxs-lookup"><span data-stu-id="d226e-105">This task has two parts.</span></span> <span data-ttu-id="d226e-106">Pierwszym etapem jest dostarczenie implementacji <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span><span class="sxs-lookup"><span data-stu-id="d226e-106">The first is to provide an implementation <xref:System.Activities.Presentation.Validation.IValidationErrorService>.</span></span>  <span data-ttu-id="d226e-107">Istnieje jedna metoda krytyczna do zaimplementowania w tym <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> interfejsie, która przekaże do <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> dziennika debugowania listę obiektów zawierających informacje o błędach.</span><span class="sxs-lookup"><span data-stu-id="d226e-107">There is one critical method to implement on this interface, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> which will pass you a list of <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> objects containing information about the errors to the debug log.</span></span>  <span data-ttu-id="d226e-108">Po wdrożeniu interfejsu można pobrać informacje o błędzie, publikując wystąpienie tej implementacji w kontekście edycji.</span><span class="sxs-lookup"><span data-stu-id="d226e-108">After implementing the interface, you retrieve the error information by publishing an instance of that implementation to the editing context.</span></span>  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a><span data-ttu-id="d226e-109">Implementowanie interfejsu IValidationErrorService</span><span class="sxs-lookup"><span data-stu-id="d226e-109">Implement the IValidationErrorService Interface</span></span>  
  
1. <span data-ttu-id="d226e-110">Oto przykład kodu dla prostej implementacji, która będzie zapisywać błędy walidacji w dzienniku debugowania.</span><span class="sxs-lookup"><span data-stu-id="d226e-110">Here is a code sample for a simple implementation that will write out the validation errors to the debug log.</span></span>  
  
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
                errors.ToList().ForEach(vei => Debug.WriteLine(string.Format("Error: {0} ", vei.Message)));  
            }  
        }  
    }  
    ```  
  
### <a name="publishing-to-the-editing-context"></a><span data-ttu-id="d226e-111">Publikowanie w kontekście edycji</span><span class="sxs-lookup"><span data-stu-id="d226e-111">Publishing to the Editing Context</span></span>  
  
1. <span data-ttu-id="d226e-112">Oto kod, który zostanie opublikowany w kontekście edycji.</span><span class="sxs-lookup"><span data-stu-id="d226e-112">Here is the code that will publish this to the editing context.</span></span>  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
