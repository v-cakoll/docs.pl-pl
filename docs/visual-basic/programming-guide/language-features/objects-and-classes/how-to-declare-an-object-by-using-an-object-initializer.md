---
title: 'Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: 3a372ba91377b53c87c05976e416ca8ed55ccbbe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)
Inicjatory obiektów umożliwiają deklarowanie i tworzy wystąpienie klasy w jednej instrukcji. Ponadto można zainicjować jednego lub więcej elementów członkowskich wystąpienia w tym samym czasie, bez wywoływania sparametryzowanym konstruktorze.  
  
 Gdy używasz inicjatora obiektów można utworzyć wystąpienia typu o nazwie domyślnego konstruktora dla klasy jest wywoływana następuje inicjowania wyznaczonych członków w kolejności, które określisz.  
  
 Poniższa procedura przedstawia sposób tworzenia wystąpienia `Student` klasy na trzy różne sposoby. Klasa ma imię, nazwisko i właściwości klas, które roku, między innymi. Każdy z trzech deklaracje tworzy nowe wystąpienie klasy `Student`, z właściwością `First` ustawioną wartość "Michael", właściwość `Last` ustawioną wartość "Tucker" i ustaw wartości domyślne wszystkich innych członków. Wynik każdej deklaracji w procedurze jest odpowiednikiem poniższy przykład, który nie korzysta z inicjatora obiektu.  
  
 [!code-vb[VbVbalrObjectInit#20](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_1.vb)]  
  
 Dla implementacji `Student` , zobacz [porady: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Możesz skopiować kod z tego tematu, aby skonfigurować klasy i utworzyć listę `Student` pracę z obiektami.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Aby utworzyć obiekt klasy o nazwie za pomocą inicjatora obiektów  
  
1.  Rozpocznij deklaracji tak, jakby planuje Użyj konstruktora.  
  
     `Dim student1 As New Student`  
  
2.  Wpisz słowa kluczowego `With`, a następnie listy inicjowanie w nawiasach klamrowych.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Na liście inicjowania obejmują każdej właściwości, którą chcesz zainicjować i przypisać wartość początkową. Nazwa właściwości jest poprzedzona kropką.  
  
     [!code-vb[VbVbalrObjectInit#21](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_2.vb)]  
  
     Możesz zainicjować co najmniej jednego członka klasy.  
  
4.  Alternatywnie można zadeklarować nowe wystąpienie klasy, a następnie przypisać wartość do niego. Po pierwsze, Zadeklaruj wystąpienie `Student`:  
  
     `Dim student2 As Student`  
  
5.  Rozpocznij tworzenie wystąpienia `Student` w zwykły sposób.  
  
     `Dim student2 As Student = New Student`  
  
6.  Typ `With` , a następnie inicjatora obiektów do zainicjowania co najmniej jednego członka nowego wystąpienia.  
  
     [!code-vb[VbVbalrObjectInit#22](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_3.vb)]  
  
7.  Można uprościć definicji w poprzednim kroku, pomijając `As Student`. Jeśli to zrobisz, kompilator Określa `student3` jest wystąpieniem `Student` przy użyciu wnioskowanie o typie lokalnym.  
  
     [!code-vb[VbVbalrObjectInit#23](../../../../visual-basic/programming-guide/language-features/objects-and-classes/codesnippet/VisualBasic/how-to-declare-an-object-by-using-an-object-initializer_4.vb)]  
  
     Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [Instrukcje: tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)  
 [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
