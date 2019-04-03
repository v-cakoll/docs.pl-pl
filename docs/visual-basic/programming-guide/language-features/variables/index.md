---
title: Zmienne w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 9a39c53ea2d57bca379297897d6d4d1b9f7a1a9f
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58840384"
---
# <a name="variables-in-visual-basic"></a>Zmienne w Visual Basic
Często muszą przechowywać wartości, wykonując obliczenia za pomocą Visual Basic. Na przykład możesz chcieć obliczanie kilka wartości, porównaj je i wykonywania różnych operacji na nich w zależności od wyniku porównania. Należy zachować wartości, jeśli chcesz je porównywać.  
  
## <a name="usage"></a>Użycie  
 Visual Basic, tak jak większość języków programowania, używa zmiennych do przechowywania wartości. A *zmiennej* o nazwie (word, którego używasz do odwoływania się do wartości, która zawiera zmienną). Zmienna również ma typ danych (który określa rodzaj danych, które mogą być przechowywane w zmiennej). Zmienna może reprezentować tablica, jeśli ma on przechowywać zaindeksowanego zestawu elementów ściśle powiązanych danych.  
  
 Wnioskowanie o typie lokalnym można deklarować zmienne bez jawne określenie typu danych. Zamiast tego kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Przypisywanie wartości  
 Instrukcje przypisania służy do wykonywania obliczeń i przypisz wynik do zmiennej, co ilustruje poniższy przykład.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
>  Znak równości (`=`) w tym przykładzie jest operatora przypisania nie był operator równości. Wartość jest przypisany do zmiennej `applesSold`.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Zmienne i właściwości  
 Zmienna, takich jak *właściwość* reprezentuje wartość, której będziesz mieć dostęp. Jednak jest bardziej skomplikowane niż zmienną. Właściwość używa bloków kodu, które kontrolują sposób ustawiania i pobierania jej wartość. Aby uzyskać więcej informacji, zobacz [różnice między właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Zobacz także

- [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Rozwiązywanie problemów związanych ze zmiennymi](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)
- [Instrukcje: Przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)
- [Różnice między właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)
- [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
