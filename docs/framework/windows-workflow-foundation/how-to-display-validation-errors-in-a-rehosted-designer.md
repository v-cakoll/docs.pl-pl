---
title: 'Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie'
ms.date: 03/30/2017
ms.assetid: 5aa8fb53-8f75-433b-bc06-7c7d33583d5d
ms.openlocfilehash: a3d993f55bf130039905f1a6512a7ae104512432
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59310203"
---
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Instrukcje: Wyświetlanie błędów walidacji w rehostowanym projektancie
W tym temacie opisano sposób pobierania i publikowanie błędów walidacji w rehostowanym [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. Zapewnia to nam za pomocą procedury, aby upewnić się, że w rehostowanym projektancie przepływu pracy jest nieprawidłowa.  
  
 To zadanie ma dwie części. Pierwszy jest zapewnienie implementację <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Brak jednej metody krytycznej do zaimplementowania w tym interfejsie <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> który zostanie przekazany listę <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach w dzienniku debugowania.  Po zaimplementowaniu interfejsu, możesz pobrać informacje o błędzie, publikując wystąpienie tę implementację Kontekst edycyjny.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Implementuj interfejs IValidationErrorService  
  
1. Poniżej przedstawiono przykładowy kod dla prostych implementacji, który będzie zapisywał się błędy sprawdzania poprawności w dzienniku debugowania.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikowanie Kontekst edycyjny  
  
1. Poniżej przedstawiono kod, który będzie publikować to Kontekst edycyjny.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
