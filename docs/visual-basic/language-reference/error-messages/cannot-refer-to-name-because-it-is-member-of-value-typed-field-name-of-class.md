---
title: "Nie można odwołać się do &#39; &lt;nazwa&gt;&#39; ponieważ jest elementem członkowskim pola &#39;&lt; Nazwa&gt;&#39; klasa &#39;&lt; ClassName&gt;&#39; mającego &#39; System.MarshalByRefObject &#39; jako klasę podstawową"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30310
- bc30310
helpviewer_keywords:
- BC30310
ms.assetid: 2aeb8872-7c87-4f01-98ef-9714ba3eebbe
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7a84811b9f0e706cf3ebede09e07c03bd7e4cea4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="cannot-refer-to-39ltnamegt39-because-it-is-a-member-of-the-value-typed-field-39ltnamegt39-of-class-39ltclassnamegt39-which-has-39systemmarshalbyrefobject39-as-a-base-class"></a>Nie można odwołać się do &#39; &lt;nazwa&gt;&#39; ponieważ jest elementem członkowskim pola &#39;&lt; Nazwa&gt;&#39; klasa &#39;&lt; ClassName&gt;&#39; mającego &#39; System.MarshalByRefObject &#39; jako klasę podstawową
`System.MarshalByRefObject` Klasa umożliwia aplikacji, które obsługują zdalny dostęp do obiektów poza granice domeny aplikacji. Typy musi dziedziczyć z `MarshalByRejectObject` klasy, gdy typ jest używany przez granice domeny aplikacji. Nie można skopiować stan obiektu, ponieważ w elementach członkowskich obiektu nie są użyteczne spoza domeny aplikacji, w którym zostały utworzone.  
  
 **Identyfikator błędu:** BC30310  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź odwołania do upewnij się, że element członkowski jest określana jest prawidłowy.  
  
2.  Jawnie zakwalifikować element członkowski o `Me` — słowo kluczowe.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.MarshalByRefObject>  
 [Dim — instrukcja](../../../visual-basic/language-reference/statements/dim-statement.md)
