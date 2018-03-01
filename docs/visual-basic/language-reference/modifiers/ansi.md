---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: aa5724eb9123b2776c3a579e4244c55b3129816b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości American National Standards Institute (ANSI) niezależnie od tego, nazwę procedury zewnętrznej, został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowany poza projektem, kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie. Informacje te obejmują lokalizacji procedurą, jak określono, jego sekwencja wywoływania oraz zwracany typ i ciąg znaków ustaw go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i przekazywać te informacje niezbędne.  
  
 `charsetmodifier` Części w `Declare` instrukcji dostarcza informacji zestaw znaków dla organizowanie ciągów podczas wywoływania procedury zewnętrznego. Wpływa to również na jak Visual Basic wyszukuje plik zewnętrznych dla nazwę procedury zewnętrznej. `Ansi` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości ANSI i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Ansi` Modyfikatora można używać w tym kontekście:  
  
 [DECLARE — instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów inteligentnych urządzeń  
 To słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz też  
 [Automatycznie](../../../visual-basic/language-reference/modifiers/auto.md)  
 [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)  
 [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
