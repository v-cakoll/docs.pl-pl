---
title: 'Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349059"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)
W przypadku tworzenia kolekcji za pomocą inicjatora kolekcji, kompilator Visual Basic wyszukuje `Add` metody typu kolekcji, dla którego parametry metody `Add` pasują do typów wartości w inicjatorze kolekcji. Ta metoda `Add` służy do wypełniania kolekcji wartościami z inicjatora kolekcji.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie pokazano `OrderCollection` kolekcję zawierającą publiczną metodę `Add`, która może być używana przez inicjator kolekcji do dodawania obiektów typu `Order`. Metoda `Add` umożliwia użycie skróconej składni inicjatora kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
