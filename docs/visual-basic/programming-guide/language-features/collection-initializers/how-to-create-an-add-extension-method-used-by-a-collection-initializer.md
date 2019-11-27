---
title: 'Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346713"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Porady: tworzenie i dodawanie metody rozszerzania wykorzystywanej przez inicjator kolekcji (Visual Basic)
W przypadku tworzenia kolekcji za pomocą inicjatora kolekcji, kompilator Visual Basic wyszukuje `Add` metody typu kolekcji, dla którego parametry metody `Add` pasują do typów wartości w inicjatorze kolekcji. Ta metoda `Add` służy do wypełniania kolekcji wartościami z inicjatora kolekcji.  
  
 Jeśli nie istnieje zgodna Metoda `Add` i nie można zmodyfikować kodu dla kolekcji, można dodać metodę rozszerzenia o nazwie `Add`, która pobiera parametry wymagane przez inicjator kolekcji. Zazwyczaj jest to konieczne, gdy do kolekcji ogólnych są używane Inicjatory kolekcji.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak dodać metodę rozszerzenia do ogólnego typu <xref:System.Collections.Generic.List%601>, aby inicjator kolekcji mógł służyć do dodawania obiektów typu `Employee`. Metoda rozszerzenia umożliwia użycie skróconej składni inicjatora kolekcji.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Zobacz także

- [Inicjatory kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Instrukcje: tworzenie kolekcji używanej przez inicjator kolekcji](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
