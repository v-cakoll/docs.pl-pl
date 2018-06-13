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
# <a name="how-to-display-validation-errors-in-a-rehosted-designer"></a>Porady: wyświetlanie błędów sprawdzania poprawności w Projektancie Rehosted
W tym temacie opisano sposób pobierania i opublikuj błędy sprawdzania poprawności w rehosted [!INCLUDE[wfd1](../../../includes/wfd1-md.md)]. To zapewnia procedury, aby upewnić się, że przepływ pracy w Projektancie rehosted jest prawidłowy.  
  
 To zadanie ma dwie części. Pierwsza to zapewniać implementację <xref:System.Activities.Presentation.Validation.IValidationErrorService>.  Brak jednej metody krytyczne do zaimplementowania w tym interfejsie <xref:System.Activities.Presentation.Validation.IValidationErrorService.ShowValidationErrors%2A> który zostanie przekazany listę <xref:System.Activities.Presentation.Validation.ValidationErrorInfo> obiektów zawierających informacje o błędach w dzienniku debugowania.  Po implementującej interfejs, możesz pobrać informacje o błędzie publikując wystąpienia tej implementacji Kontekst edycyjny.  
  
### <a name="implement-the-ivalidationerrorservice-interface"></a>Zaimplementuj interfejs IValidationErrorService  
  
1.  Oto przykład kodu dla prostych implementacji, która zapisze błędy sprawdzania poprawności w dzienniku debugowania.  
  
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
  
### <a name="publishing-to-the-editing-context"></a>Publikowanie w kontekście edycji  
  
1.  Oto kod, który będzie publikować to Kontekst edycyjny.  
  
    ```  
    wd.Context.Services.Publish<IValidationErrorService>(new DebugValidationErrorService());  
    ```
