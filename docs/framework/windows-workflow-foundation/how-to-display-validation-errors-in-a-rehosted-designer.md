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
