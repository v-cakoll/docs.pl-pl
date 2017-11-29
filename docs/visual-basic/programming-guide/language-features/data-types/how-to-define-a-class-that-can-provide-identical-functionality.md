---
title: "Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- data type arguments [Visual Basic], using
- type parameters [Visual Basic], defining
- data type arguments [Visual Basic], defining
- arguments [Visual Basic], data types
- Of keyword [Visual Basic], using
- constraints, Visual Basic generic types
- generic parameters
- data type parameters
- data type parameters [Visual Basic], using
- generics [Visual Basic], defining classes with type parameters
- data types [Visual Basic], as parameters
- data types [Visual Basic], as arguments
- parameters [Visual Basic], type
- type arguments
- types [Visual Basic], generic
- parameters [Visual Basic], generic
- type parameters
- data type arguments
- parameters [Visual Basic], data type
- generics [Visual Basic], defining generic types
- data type parameters [Visual Basic], defining
- type arguments [Visual Basic], defining
- arguments [Visual Basic], type
ms.assetid: a914adf8-e68f-4819-a6b1-200d1cf1c21c
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 7cc2563f193fba9f9e30fcdfd5ea2766be16ba63
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Porady: definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)
Można zdefiniować klasę z którego można tworzyć obiektów, które zapewnić identyczną funkcjonalność różnych typów danych. Aby to zrobić, należy określić co najmniej jeden *parametry typu* w definicji. Klasa może następnie służyć jako szablon dla obiektów, które używają różnych typów danych. Klasy określonej w ten sposób jest nazywany *klasy ogólnej*.  
  
 Zaletą definiowania klasy generycznej jest tylko raz określić, czy kod można go użyć do utworzenia wiele obiektów, które używają różnych typów danych. Powoduje to lepszą wydajność niż definiowanie klas z `Object` typu.  
  
 Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsów, procedury i delegatów.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Aby zdefiniować klasę z parametrem typu  
  
1.  Zdefiniuj klasę w zwykły sposób.  
  
2.  Dodaj `(Of` *typeparameter* `)` zaraz po nazwie klasy, aby określić parametr typu.  
  
3.  Jeśli masz więcej niż jeden parametr typu należy wewnątrz nawiasów listy rozdzielanej przecinkami. Nie powtarzaj `Of` — słowo kluczowe.  
  
4.  Jeśli kod wykonuje operacje na parametr typu innego niż prosty przypisania, wykonaj parametru typu z `As` klauzuli, aby dodać jeden lub więcej *ograniczenia*. Ograniczenie gwarantuje, że podany dla tego parametru typu typ spełnia wymagania, takie jak następujące:  
  
    -   Obsługuje operacji, takich jak `>`, który wykonuje kodu  
  
    -   Obsługuje członka, takich jak metoda, która uzyskuje dostęp do kodu  
  
    -   Przedstawia konstruktora bez parametrów  
  
     Jeśli nie określono żadnych ograniczeń, tylko operacje i elementów członkowskich, można użyć kodu są obsługiwanymi przez [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Aby uzyskać więcej informacji, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Zidentyfikuj co element członkowski klasy, która ma być deklarowany za pomocą podanego typu i Zadeklaruj `As` `typeparameter`. Dotyczy to pamięci wewnętrznej, procedury parametrów i zwracanych wartości.  
  
6.  Pamiętaj, że kod używa tylko operacje i metody, które są obsługiwane przez dowolny typ danych może dostarczyć do `itemType`.  
  
     W poniższym przykładzie zdefiniowano klasę, która zarządza listą bardzo proste. Przechowuje listy w tablicy wewnętrznej `items`i przy użyciu kodu można zadeklarować typu danych elementów listy. Umożliwia korzystanie z sparametryzowanym konstruktorze kod, aby ustawić górna granica `items`, i ustawia domyślny konstruktor, to do 9 (dla wszystkich elementów 10).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Można zadeklarować klasy z `simpleList` do przechowywania listy `Integer` wartości inną klasę do przechowywania listy `String` wartości, a druga do przechowywania `Date` wartości. Z wyjątkiem typu danych listy elementów członkowskich obiekty utworzone na podstawie tych klas zachowują się tak samo.  
  
     Argument typu, który za pomocą kodu dostarcza do `itemType` może być typu wewnętrznego takich jak `Boolean` lub `Double`, struktury, wyliczenia lub dowolnego typu klasy, w tym, który definiuje aplikacji.  
  
     Można przetestować klasy `simpleList` następującym kodem.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Niezależność od języka i elementy niezależne od języka](https://msdn.microsoft.com/library/12a7a7h3)  
 [Z](../../../../visual-basic/language-reference/statements/of-clause.md)  
 [Lista typów](../../../../visual-basic/language-reference/statements/type-list.md)  
 [Porady: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)  
 [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
