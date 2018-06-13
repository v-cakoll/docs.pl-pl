---
title: Zmienne w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: 79cd5629d4de6279eb370c18db617a5ad532108d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654476"
---
# <a name="variables-in-visual-basic"></a>Zmienne w Visual Basic
Często mają do przechowywania wartości podczas wykonywania obliczeń za pomocą Visual Basic. Na przykład można obliczyć wartości kilku, porównaj je i wykonywać różne operacje, w zależności od wyniku porównania. Należy zachować wartości, jeśli chcesz porównać je.  
  
## <a name="usage"></a>Użycie  
 Visual Basic, podobnie jak większość języków programowania, używa zmienne do przechowywania wartości. A *zmiennej* ma nazwę (word, którego używasz do odwoływania się do wartości, która zawiera zmienną). Zmienna również ma typ danych (który określa rodzaj danych, które mogą być przechowywane w zmiennej). Zmienna może reprezentować tablicy, jeśli ma ona do przechowywania indeksowanego zbiór elementów danych jest blisko związane.  
  
 Wnioskowanie o typie lokalnym umożliwia Zadeklaruj zmienne bez jawne określenie typu danych. Zamiast tego kompilator wnioskuje typ zmiennej typu wyrażenia inicjowania. Aby uzyskać więcej informacji, zobacz [wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md) i [Option Infer — instrukcja](../../../../visual-basic/language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Przypisywanie wartości  
 Instrukcje przypisania służy do wykonywania obliczeń i przypisz wynik do zmiennej, jak przedstawiono na poniższym przykładzie.  
  
 [!code-vb[VbVbalrVariables#1](../../../../visual-basic/programming-guide/language-features/variables/codesnippet/VisualBasic/index_1.vb)]  
  
> [!NOTE]
>  Znak równości (`=`) w tym przykładzie jest operatora przypisania nie był operator równości. Wartość jest przypisany do zmiennej `applesSold`.  
  
 Aby uzyskać więcej informacji, zobacz [porady: przenoszenie danych do i z zmiennej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Właściwości i zmienne  
 Zmienna, takich jak *właściwość* reprezentuje wartość, której będziesz mieć dostęp. Jest jednak bardziej skomplikowane niż zmiennej. Właściwość używa bloki kodu, które kontrolują sposób ustawiania i pobierania jej wartość. Aby uzyskać więcej informacji, zobacz [różnice pomiędzy właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Rozwiązywanie problemów związanych ze zmiennymi](../../../../visual-basic/programming-guide/language-features/variables/troubleshooting-variables.md)  
 [Instrukcje: przenoszenie danych do zmiennej i z niej](../../../../visual-basic/programming-guide/language-features/variables/how-to-move-data-into-and-out-of-a-variable.md)  
 [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](../../../../visual-basic/programming-guide/language-features/procedures/differences-between-properties-and-variables.md)  
 [Wnioskowanie o typie lokalnym](../../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
