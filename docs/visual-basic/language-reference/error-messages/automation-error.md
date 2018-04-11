---
title: Błąd automatyzacji
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbrID440
ms.assetid: 2c4be5c5-2f0d-4a2b-96fe-d1b24f08fc4c
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 790b171b8d4022bd6d8b038c4221f24805ae42f5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="automation-error"></a>Błąd automatyzacji
Wystąpił błąd podczas wykonywania metody lub pobierania lub ustawiania właściwości zmiennej obiektu. Błąd został zgłoszony przez aplikację, który utworzył obiekt.  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź właściwości `Err` obiektem, aby określić źródło i charakteru błędu.  
  
2.  Użyj `On Error Resume Next` instrukcji bezpośrednio przed podczas uzyskiwania dostępu do instrukcji, a następnie Wyszukaj błędy bezpośrednio po instrukcji podczas uzyskiwania dostępu do.  
  
## <a name="see-also"></a>Zobacz też  
 [Error — typy](../../../visual-basic/programming-guide/language-features/error-types.md)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
