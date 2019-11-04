---
title: 'Instrukcje: wyświetlanie błędów walidacji w rehostowanym projektancie'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: d36883eb77864ccc16cb5882d0de216e1aaaa589
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73420607"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Instrukcje: wyświetlanie błędów walidacji w rehostowanym projektancie
W tym temacie opisano sposób pobierania i publikowania błędów walidacji w rehostie [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. Dzięki temu można sprawdzić, czy przepływ pracy w przewidzianym przez niego projektancie jest prawidłowy.  
  
 To zadanie ma dwie części. Pierwszym etapem jest dostarczenie <xref:System.Activities.Presentation.Validation.IValidationErrorService>implementacji.  Istnieje jedna metoda krytyczna do zaimplementowania w tym interfejsie, <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> co spowoduje przekazanie listy <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach do dziennika debugowania.  Po wdrożeniu interfejsu można pobrać informacje o błędzie, publikując wystąpienie tej implementacji w kontekście edycji.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementowanie interfejsu IValidationErrorService  
  
1. Oto przykład kodu dla prostej implementacji, która będzie zapisywać błędy walidacji w dzienniku debugowania.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikowanie w kontekście edycji  
  
1. Oto kod, który zostanie opublikowany w kontekście edycji.  
  
    ```csharp  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
