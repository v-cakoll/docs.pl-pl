---
title: 'Porady: deklarowanie obiektu za pomocą inicjatora obiektów'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: ae04d338b61027c3917ad3a7f62ff40f0a95e53e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347136"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)
Inicjatory obiektów umożliwiają zadeklarować wystąpienie klasy w pojedynczej instrukcji i utworzenie ich wystąpienia. Ponadto można zainicjować co najmniej jeden element członkowski wystąpienia w tym samym czasie, bez wywoływania sparametryzowanego konstruktora.  
  
 Gdy używasz inicjatora obiektów do utworzenia wystąpienia nazwanego typu, Konstruktor bez parametrów dla klasy jest wywoływany, a po nim inicjacja wyznaczono członków w określonej kolejności.  
  
 Poniższa procedura pokazuje, jak utworzyć wystąpienie klasy `Student` na trzy różne sposoby. Klasa ma imię, nazwisko i właściwości roku klasy, między innymi. Każda z trzech deklaracji tworzy nowe wystąpienie `Student`, z właściwością `First` ustawioną na "Michael", właściwość `Last` ustawiona na wartość "Tucker", a wszystkie inne elementy członkowskie mają ustawioną wartość domyślną. Wynik każdej deklaracji w procedurze jest równoważny do poniższego przykładu, który nie używa inicjatora obiektów.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Aby uzyskać implementację klasy `Student`, zobacz [How to: Create a list of Items](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md). Możesz skopiować kod z tego tematu, aby skonfigurować klasę i utworzyć listę obiektów `Student` do pracy.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Aby utworzyć obiekt nazwanej klasy przy użyciu inicjatora obiektów  
  
1. Rozpocznij deklarację tak, jakby była planowana użycie konstruktora.  
  
     `Dim student1 As New Student`  
  
2. Wpisz `With`słowa kluczowego, a następnie listę inicjalizacji w nawiasach klamrowych.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Na liście inicjalizacji Uwzględnij każdą właściwość, która ma zostać zainicjowana, i przypisz do niej początkową wartość. Nazwa właściwości jest poprzedzona kropką.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Można zainicjować co najmniej jeden element członkowski klasy.  
  
4. Alternatywnie można zadeklarować nowe wystąpienie klasy, a następnie przypisać do niej wartość. Najpierw Zadeklaruj wystąpienie `Student`:  
  
     `Dim student2 As Student`  
  
5. Rozpocznij tworzenie wystąpienia `Student` w normalny sposób.  
  
     `Dim student2 As Student = New Student`  
  
6. Wpisz `With` a następnie Inicjator obiektu, aby zainicjować co najmniej jednego członka nowego wystąpienia.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Można uprościć definicję w poprzednim kroku, pomijając `As Student`. W takim przypadku kompilator określi, że `student3` jest wystąpieniem `Student` za pomocą wnioskowania typu lokalnego.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md).  
  
## <a name="see-also"></a>Zobacz także

- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Instrukcje: tworzenie listy elementów](../../../../visual-basic/programming-guide/concepts/linq/how-to-create-a-list-of-items.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)
