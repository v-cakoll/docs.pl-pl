---
title: 'Porady: definiowanie parametru dla procedury (Visual Basic)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- procedure parameters [Visual Basic], defining data types for
- procedures [Visual Basic], parameters
- procedures [Visual Basic], defining
- Visual Basic code, procedures
- procedure parameters [Visual Basic], defining
ms.assetid: 7962808d-407e-4e84-984e-43e9857c53c9
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3c909cfe1b45a42aae91948917f310474575f225
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-parameter-for-a-procedure-visual-basic"></a>Porady: definiowanie parametru dla procedury (Visual Basic)
A *parametru* umożliwia kod wywołujący przekazać wartości do procedury, gdy wywołuje ona. Każdy parametr dla procedury zadeklarować zadeklarować zmiennej, określając jej nazwę i typ danych tak samo. Można także określić mechanizm przekazywania i określa, czy parametr jest opcjonalny.  
  
 Aby uzyskać więcej informacji, zobacz [parametry i argumenty procedur](./procedure-parameters-and-arguments.md).  
  
### <a name="to-define-a-procedure-parameter"></a>Aby zdefiniować parametr procedury  
  
1.  W deklaracji procedury Dodaj nazwę parametru do listy parametrów procedury, oddzielając go od innych parametrów przecinkami.  
  
2.  Określ typ danych parametru.  
  
3.  Postępuj zgodnie z nazwy parametru `As` klauzuli, aby określić typ danych.  
  
4.  Zdecyduj, mechanizm przekazywania, dla parametru. Zazwyczaj należy przekazać parametr wg wartości, chyba że chcesz procedury, aby można było zmienić jego wartość w wywoływanym kodzie.  
  
5.  Poprzedź nazwę parametru z [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md) lub [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md) Aby określić mechanizm przekazywania. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy przekazywaniem argumentu według wartości i według odwołania](./differences-between-passing-an-argument-by-value-and-by-reference.md).  
  
6.  Jeśli parametr jest opcjonalny, poprzedź mechanizm przekazywania z [opcjonalnie](../../../../visual-basic/language-reference/modifiers/optional.md) i postępuj zgodnie z typem danych parametru znakiem równości (`=`) i wartość domyślną.  
  
     W poniższym przykładzie zdefiniowano konturu `Sub` procedury z trzema parametrami. Wymagane są dwa pierwsze i trzeci jest opcjonalny. Deklaracji parametrów są rozdzielane na liście parametrów przecinkami.  
  
     [!code-vb[VbVbcnProcedures#33](./codesnippet/VisualBasic/how-to-define-a-parameter-for-a-procedure_1.vb)]  
  
     Pierwszy parametr akceptuje `customer` obiektu, a `updateCustomer` można bezpośrednio zaktualizować zmiennej przekazany do `c` ponieważ argument jest przekazywany [ByRef](../../../../visual-basic/language-reference/modifiers/byref.md). Procedury nie można zmienić wartości dwa ostatnie argumenty, ponieważ są one przekazywane [ByVal](../../../../visual-basic/language-reference/modifiers/byval.md).  
  
     Jeśli kod wywołujący nie dostarcza wartość `level` parametru [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] ustawia ją na wartość domyślną równą 0.  
  
     Jeśli sprawdzanie typu przełącznik ([Option Strict — instrukcja](../../../../visual-basic/language-reference/statements/option-strict-statement.md)) jest `Off`, `As` klauzuli jest opcjonalny, gdy Definiowanie parametru. Jednak jeśli korzysta z żadnych jeden parametr `As` klauzuli wszystkich z nich należy użyć go. Jeśli typ sprawdzania przełącznika `On`, `As` klauzula jest wymagany dla każdej definicji parametru.  
  
     Określanie typów danych dla wszystkich elementów programowania nosi nazwę *silne wpisywanie*. Podczas ustawiania `Option Strict On`, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wymusza silne wpisywanie. Jest to zdecydowanie zalecane, z następujących powodów:  
  
    -   Umożliwia obsługę funkcji IntelliSense na parametry i zmienne. Dzięki temu można zobaczyć ich właściwości oraz o innych elementach członkowskich jako typu w kodzie.  
  
    -   Umożliwia kompilatorowi sprawdzania typu. Dzięki temu catch instrukcji, które może zakończyć się niepowodzeniem w czasie wykonywania z powodu błędów, takich jak przepełnienia. Przechwytuje również wywołania metod, w obiektach, które nie są obsługiwane.  
  
    -   Wynikiem szybsze wykonywanie kodu. Powodem tego jest to, że jeśli nie określisz typu danych dla elementu programistycznego, [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] kompilatora przypisuje go `Object` typu. Skompilowany kod może być konieczne Konwertuj i z powrotem między `Object` a innymi typami danych, co zmniejsza wydajność.  
  
## <a name="see-also"></a>Zobacz też  
 [Procedury](./index.md)  
 [Sub — procedury](./sub-procedures.md)  
 [Procedury funkcji](./function-procedures.md)  
 [Porady: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)  
 [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)  
 [Procedury cykliczne](./recursive-procedures.md)  
 [Przeciążanie procedury](./procedure-overloading.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Programowanie zorientowane obiektowo](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)
