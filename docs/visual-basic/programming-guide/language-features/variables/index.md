---
title: Zmienne w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 30baab24c54b5158da53f1ba88206d8f1564ebaf
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69953349"
---
# <a name="variables-in-visual-basic"></a>Zmienne w Visual Basic
Często należy przechowywać wartości podczas wykonywania obliczeń z Visual Basic. Na przykład możesz chcieć obliczyć kilka wartości, porównać je i wykonywać na nich różne operacje, w zależności od wyniku porównania. Należy zachować wartości, jeśli chcesz je porównać.  
  
## <a name="usage"></a>Użycie  
 Visual Basic, podobnie jak większość języków programowania, używa zmiennych do przechowywania wartości. *Zmienna* ma nazwę (wyraz używany do odwoływania się do wartości, która zawiera zmienna). Zmienna ma również typ danych (który określa rodzaj danych, które mogą być przechowywane w zmiennej). Zmienna może reprezentować tablicę, jeśli musi przechowywać indeksowany zestaw ściśle powiązanych elementów danych.  
  
 Wnioskowanie o typie lokalnym umożliwia deklarowanie zmiennych bez jawnego określenia typu danych. Zamiast tego, kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Aby uzyskać więcej informacji, zobacz [lokalne wnioskowanie o typie](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i zestawienie [opcji](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Przypisywanie wartości  
 Instrukcje przypisania służą do wykonywania obliczeń i przypisywania wyniku do zmiennej, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Znak równości (`=`) w tym przykładzie jest operatorem przypisania, a nie operatorem równości. Wartość jest przypisana do zmiennej `applesSold`.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Przenoszenie danych do zmiennej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)i z niej.  
  
## <a name="variables-and-properties"></a>Zmienne i właściwości  
 Podobnie jak zmienna, *Właściwość* reprezentuje wartość, do której można uzyskać dostęp. Jest to jednak bardziej złożone niż zmienna. Właściwość używa bloków kodu, które kontrolują sposób ustawiania i pobierania jego wartości. Aby uzyskać więcej informacji, zobacz [różnice między właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Rozwiązywanie problemów związanych ze zmiennymi](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Instrukcje: Przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
