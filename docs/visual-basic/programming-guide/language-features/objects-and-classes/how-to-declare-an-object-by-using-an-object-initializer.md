---
title: 'Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: e0673c9faceb3bd9fc71123a2ae22abbc7061c04
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56970210"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Instrukcje: Deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)
Inicjatory obiektów umożliwiają deklarowanie i tworzy wystąpienie klasy w pojedynczej instrukcji. Ponadto należy zainicjować co najmniej jednego członka wystąpienia w tym samym czasie, bez wywoływania sparametryzowania konstruktora.  
  
 Gdy używasz inicjatora obiektu można utworzyć wystąpienia typu nazwanego, wywoływany jest konstruktor domyślny klasy, następuje inicjowanie wyznaczonych członków w kolejności, które określisz.  
  
 Poniższa procedura przedstawia sposób tworzenia wystąpienia `Student` klasy na trzy różne sposoby. Klasa ma imię, nazwisko i właściwości klas, które roku, między innymi. Każdy z trzech deklaracje tworzy nowe wystąpienie klasy `Student`, z właściwością `First` ustawiona na "Jan", właściwość `Last` ustawiona na "Tucker", a wszystkie inne elementy członkowskie zestawu do wartości domyślnych. Wynik każdego zgłoszenia w procedurze jest równoważne z poniższego przykładu, który nie korzysta z inicjatora obiektu.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Na implementację `Student` klasy, zobacz [jak: Utwórz listę elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Możesz skopiować kod z tego tematu, aby skonfigurować klasy i tworzenie listy `Student` pracę z obiektami.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Aby utworzyć obiekt klasy o nazwie za pomocą inicjatora obiektów  
  
1.  Rozpocznij zgłoszenia w tak, jakby planuje użyć konstruktora.  
  
     `Dim student1 As New Student`  
  
2.  Wpisz słowo kluczowe `With`, a następnie listy inicjowania w nawiasach klamrowych.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3.  Na liście inicjowania obejmują każdej właściwości, którą chcesz zainicjować i przypisać jej wartość początkową. Nazwa właściwości jest poprzedzony przez okres.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Można zainicjować co najmniej jednego członka klasy.  
  
4.  Alternatywnie można zadeklarować nowe wystąpienie klasy i następnie przypisać jej wartości. Najpierw należy zadeklarować wystąpienie `Student`:  
  
     `Dim student2 As Student`  
  
5.  Rozpocznij tworzenie wystąpienia `Student` w normalny sposób.  
  
     `Dim student2 As Student = New Student`  
  
6.  Typ `With` i następnie inicjatora obiektu można zainicjować co najmniej jednego członka nowego wystąpienia.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7.  Można uprościć definicji w poprzednim kroku, pomijając `As Student`. Jeśli to zrobisz, kompilator Określa `student3` jest wystąpieniem `Student` przy użyciu wnioskowanie o typie lokalnym.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Zobacz także
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrukcje: Tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Inicjatory obiektów: Typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
