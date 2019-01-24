---
title: 'Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 9f6faf7b9ba2338784fda2cec2efc2b3991d415e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667482"
---
# <a name="how-to-define-a-class-that-can-provide-identical-functionality-on-different-data-types-visual-basic"></a>Instrukcje: Definiowanie klasy, która może zapewnić identyczną funkcjonalność różnych typów danych (Visual Basic)
Można zdefiniować klasę, w którym możesz tworzyć obiekty, które zapewnić identyczną funkcjonalność różnych typów danych. Aby to zrobić, należy określić co najmniej jeden *parametry typu* w definicji. Klasy mogą następnie służyć jako szablon dla obiektów, które używają różnych typów danych. Nosi nazwę klasy zdefiniowanej w ten sposób *klasy generycznej*.  
  
 Zaletą definiowania klasy ogólnej jest, że można określić tylko raz, a kod służy do tworzenia wielu obiektów, które używają różnych typów danych. Skutkuje to lepszą wydajność niż Definiowanie klasy za pomocą `Object` typu.  
  
 Oprócz klas można również zdefiniować i używać struktury ogólne, interfejsy, procedury i delegatów.  
  
### <a name="to-define-a-class-with-a-type-parameter"></a>Aby zdefiniować klasę z parametrem typu  
  
1.  Zdefiniuj klasę w normalny sposób.  
  
2.  Dodaj `(Of` *typeparameter* `)` zaraz po nazwie klasy, aby określić parametr typu.  
  
3.  Jeśli masz więcej niż jeden parametr typu, należy utworzyć listę rozdzielonych przecinkami wewnątrz nawiasów. Nie powtarzaj `Of` — słowo kluczowe.  
  
4.  Jeśli Twój kod wykonuje operacje na parametr typu innego niż przypisanie proste, postępuj zgodnie z tego parametru typu z `As` klauzuli, aby dodać co najmniej jedno *ograniczenia*. Ograniczenie gwarantuje, że podany dla tego parametru typu typ spełnia wymagania, takie jak następujące:  
  
    -   Obsługuje operacji, takich jak `>`, który wykonuje kod  
  
    -   Obsługuje elementu członkowskiego, takie jak metody, która uzyskuje dostęp do kodu  
  
    -   Udostępnia konstruktora bez parametrów  
  
     Jeśli nie określisz żadnych ograniczeń, tylko operacji i kod użytkownika może używać elementów członkowskich są obsługiwane przez [Object — typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md). Aby uzyskać więcej informacji, zobacz [lista typów](../../../../visual-basic/language-reference/statements/type-list.md).  
  
5.  Identyfikowanie każdy członek klasy, która ma być deklarowany za pomocą podanego typu i Zadeklaruj go `As` `typeparameter`. Dotyczy to pamięci wewnętrznej, procedury parametrów i zwracanych wartości.  
  
6.  Pamiętaj, że kod używa tylko operacje i metody, które są obsługiwane przez dowolny typ danych, można dostarczyć do `itemType`.  
  
     W poniższym przykładzie zdefiniowano klasę, która zarządza listą bardzo proste. Przechowuje listę w tablicy wewnętrznej `items`oraz przy użyciu kodu można zadeklarować typ danych elementów listy. Sparametryzowania konstruktora umożliwia przy użyciu kodu, aby ustawić górną granicę `items`, i ustawia domyślny konstruktor, to do 9 (w sumie 10 elementów).  
  
     [!code-vb[VbVbalrDataTypes#7](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_1.vb)]  
  
     Można zadeklarować klasy z `simpleList` do przechowywania listy `Integer` wartości innej klasy do przechowywania listy `String` wartości, a druga do przechowywania `Date` wartości. Z wyjątkiem typu danych listy elementów członkowskich obiekty utworzone na podstawie tych klas zachowują się identycznie.  
  
     Argument typu, który używając kodu dostarcza do `itemType` może być typu wewnętrznego taką jak `Boolean` lub `Double`, struktury, wyliczenia lub dowolnego typu klasy, w tym taki, który jest określane przez aplikację.  
  
     Możesz przetestować klasy `simpleList` następującym kodem.  
  
     [!code-vb[VbVbalrDataTypes#8](../../../../visual-basic/language-reference/data-types/codesnippet/VisualBasic/how-to-define-a-class-that-can-provide-identical-functionality_2.vb)]  
  
## <a name="see-also"></a>Zobacz także
- [Typy danych](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [Typy ogólne w Visual Basic](../../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Niezależność od języka i składniki niezależne od języka](../../../../standard/language-independence-and-language-independent-components.md)
- [z](../../../../visual-basic/language-reference/statements/of-clause.md)
- [Lista typów](../../../../visual-basic/language-reference/statements/type-list.md)
- [Instrukcje: używanie klasy ogólnej](../../../../visual-basic/programming-guide/language-features/data-types/how-to-use-a-generic-class.md)
- [Object, typ danych](../../../../visual-basic/language-reference/data-types/object-data-type.md)
