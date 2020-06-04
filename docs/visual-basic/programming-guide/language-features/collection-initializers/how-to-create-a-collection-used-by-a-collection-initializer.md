---
title: 'Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 7cba290b92f41125a93d1ed022e4db5ef62da789
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414559"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Porady: tworzenie kolekcji wykorzystywanej przez inicjator kolekcji (Visual Basic)
W przypadku tworzenia kolekcji za pomocą inicjatora kolekcji, kompilator Visual Basic wyszukuje `Add` metodę typu kolekcji, dla którego parametry `Add` metody pasują do typów wartości w inicjatorze kolekcji. Ta `Add` Metoda służy do wypełniania kolekcji wartościami z inicjatora kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje `OrderCollection` kolekcję zawierającą metodę publiczną `Add` , która może być używana przez inicjator kolekcji do dodawania obiektów typu `Order` . `Add`Metoda umożliwia użycie skróconej składni inicjatora kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz też

- [Inicjatory kolekcji](index.md)
- [Instrukcje: tworzenie i dodawanie metody rozszerzenia używanej przez inicjator kolekcji](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
