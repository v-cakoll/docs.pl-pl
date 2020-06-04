---
title: 'Porady: deklarowanie obiektu za pomocą inicjatora obiektów'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring objects using object initializer
- object initializers [Visual Basic]
- initializers [Visual Basic]
- Video How tos, Visual Basic
ms.assetid: 0f53a553-efd6-466d-80bf-6b679e5cd174
ms.openlocfilehash: cf4954059a4b0bf015bed82a74357ecfd5f5987e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404878"
---
# <a name="how-to-declare-an-object-by-using-an-object-initializer-visual-basic"></a>Porady: deklarowanie obiektu za pomocą inicjatora obiektów (Visual Basic)
Inicjatory obiektów umożliwiają zadeklarować wystąpienie klasy w pojedynczej instrukcji i utworzenie ich wystąpienia. Ponadto można zainicjować co najmniej jeden element członkowski wystąpienia w tym samym czasie, bez wywoływania sparametryzowanego konstruktora.  
  
 Gdy używasz inicjatora obiektów do utworzenia wystąpienia nazwanego typu, Konstruktor bez parametrów dla klasy jest wywoływany, a po nim inicjacja wyznaczono członków w określonej kolejności.  
  
 Poniższa procedura pokazuje, jak utworzyć wystąpienie `Student` klasy na trzy różne sposoby. Klasa ma imię, nazwisko i właściwości roku klasy, między innymi. Każda z trzech deklaracji tworzy nowe wystąpienie `Student` , z właściwością `First` ustawioną na "Michael", właściwość `Last` ustawioną na wartość "Tucker", a wszystkie inne elementy członkowskie mają ustawioną wartość domyślną. Wynik każdej deklaracji w procedurze jest równoważny do poniższego przykładu, który nie używa inicjatora obiektów.  
  
 [!code-vb[VbVbalrObjectInit#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#20)]  
  
 Aby uzyskać implementację `Student` klasy, zobacz [How to: Create a list of Items](../../concepts/linq/how-to-create-a-list-of-items.md). Możesz skopiować kod z tego tematu, aby skonfigurować klasę i utworzyć listę `Student` obiektów do pracy.  
  
### <a name="to-create-an-object-of-a-named-class-by-using-an-object-initializer"></a>Aby utworzyć obiekt nazwanej klasy przy użyciu inicjatora obiektów  
  
1. Rozpocznij deklarację tak, jakby była planowana użycie konstruktora.  
  
     `Dim student1 As New Student`  
  
2. Wpisz słowo kluczowe `With` , a następnie listę inicjalizacji w nawiasach klamrowych.  
  
     `Dim student1 As New Student With { <initialization list> }`  
  
3. Na liście inicjalizacji Uwzględnij każdą właściwość, która ma zostać zainicjowana, i przypisz do niej początkową wartość. Nazwa właściwości jest poprzedzona kropką.  
  
     [!code-vb[VbVbalrObjectInit#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#21)]  
  
     Można zainicjować co najmniej jeden element członkowski klasy.  
  
4. Alternatywnie można zadeklarować nowe wystąpienie klasy, a następnie przypisać do niej wartość. Najpierw Zadeklaruj wystąpienie `Student` :  
  
     `Dim student2 As Student`  
  
5. Rozpocznij tworzenie wystąpienia `Student` w normalny sposób.  
  
     `Dim student2 As Student = New Student`  
  
6. Wpisz `With` , a następnie Inicjator obiektu, aby zainicjować co najmniej jednego członka nowego wystąpienia.  
  
     [!code-vb[VbVbalrObjectInit#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#22)]  
  
7. Można uprościć definicję w poprzednim kroku, pomijając `As Student` . Jeśli to zrobisz, kompilator określa, że `student3` jest wystąpieniem przy `Student` użyciu wnioskowania typu lokalnego.  
  
     [!code-vb[VbVbalrObjectInit#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrObjectInit/VB/Class2.vb#23)]  
  
     Aby uzyskać więcej informacji, zobacz temat [wnioskowanie o typie lokalnym](../variables/local-type-inference.md).  
  
## <a name="see-also"></a>Zobacz też

- [Wnioskowanie o typie lokalnym](../variables/local-type-inference.md)
- [Instrukcje: tworzenie listy elementów](../../concepts/linq/how-to-create-a-list-of-items.md)
- [Inicjatory obiektów: typy nazwane i anonimowe](object-initializers-named-and-anonymous-types.md)
- [Typy anonimowe](anonymous-types.md)
