---
title: Ansi (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Ansi
helpviewer_keywords:
- Declare statement [Visual Basic], marshaling strings [Visual Basic]
- ANSI, Visual Basic
- ANSI
ms.assetid: 4f1fa6ff-5557-41ab-b6da-90baf4c15917
ms.openlocfilehash: 98dafab3e524ea371bba228eb231e28d46cc3b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802560"
---
# <a name="ansi-visual-basic"></a>Ansi (Visual Basic)
Określa, że Visual Basic powinien kierować wszystkie ciągi wartości American National Standards Institute (ANSI), niezależnie od nazwy procedury zewnętrznego został zadeklarowany.  
  
 Po wywołaniu procedury zdefiniowane poza projektem, kompilator Visual Basic nie ma dostępu do informacji wymaganych do wywołania tej procedury poprawnie. Informacje te obejmują, gdzie znajduje się procedura, sposób jego identyfikacji, jego sekwencja wywoływania i zwracany typ i zestaw znaków ciągu, od go używa. [Instrukcji Declare](../../../visual-basic/language-reference/statements/declare-statement.md) tworzy odwołanie do zewnętrznej procedury i dostarcza to informacje niezbędne.  
  
 `charsetmodifier` Wchodzi w skład w `Declare` instrukcji dostarcza informacji zestaw znaków dla marshaling ciągów podczas wywoływania procedury zewnętrznego. Ma to również wpływ jak języka Visual Basic poszukuje zewnętrznego pliku, aby uzyskać nazwę procedury zewnętrznej. `Ansi` Modyfikator Określa, że Visual Basic powinien kierować wszystkie ciągi jako wartości ANSI i sprawdzić procedurę bez modyfikowania jej nazwy podczas wyszukiwania.  
  
 Jeśli określono nie modyfikator zestawu znaków, `Ansi` jest ustawieniem domyślnym.  
  
## <a name="remarks"></a>Uwagi  
 `Ansi` Modyfikatora można używać w tym kontekście:  
  
 [Declare, instrukcja](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
## <a name="smart-device-developer-notes"></a>Uwagi dla deweloperów urządzeń inteligentnych  
 This — słowo kluczowe nie jest obsługiwane.  
  
## <a name="see-also"></a>Zobacz także

- [Auto](../../../visual-basic/language-reference/modifiers/auto.md)
- [Unicode](../../../visual-basic/language-reference/modifiers/unicode.md)
- [Słowa kluczowe](../../../visual-basic/language-reference/keywords/index.md)
