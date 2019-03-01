---
title: 'Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: d0007ebf5f18dee5bd8448a071fe1f0f984aff1a
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56967454"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Instrukcje: Tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)
Gdy używasz inicjatora kolekcji, aby utworzyć kolekcję, kompilator Visual Basic, wyszukuje `Add` metody typu kolekcji, dla której parametry `Add` metoda pasują do typów wartości na liście inicjatora kolekcji. To `Add` metoda jest używana do wypełniania kolekcji z wartościami z inicjatora kolekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie przedstawiono `OrderCollection` kolekcji, która zawiera publiczny `Add` metodę, która inicjator kolekcji służy do dodawania obiektów typu `Order`. `Add` Metoda pozwala przy użyciu składni inicjatora kolekcji skrócona.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także
- [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Instrukcje: Utwórz Dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
