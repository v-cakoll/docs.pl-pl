---
title: 'Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58825407"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)
Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic, wyszukuje `Add` metody typu kolekcji, dla której parametry `Add` metoda pasują do typów wartości na liście inicjatora kolekcji. To `Add` metoda jest używana do wypełniania kolekcji z wartościami z inicjatora kolekcji.  
  
 Jeśli brak zgodności `Add` metoda istnieje i nie można zmodyfikować kod dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add` która przyjmuje parametry, które są wymagane przez inicjator kolekcji. Jest to zazwyczaj, co należy zrobić, gdy używasz inicjatory kolekcji dla kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać metody rozszerzenia do ogólnego <xref:System.Collections.Generic.List%601> wpisz, aby inicjatora kolekcji można dodawać obiekty określonego typu `Employee`. Metoda rozszerzenia umożliwia przy użyciu składni inicjatora kolekcji skrócona.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
