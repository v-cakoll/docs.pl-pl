---
title: Zmienne
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
ms.openlocfilehash: ff617774d7e93ab4238ebc06617cc03fb6bc675a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410389"
---
# <a name="variables-in-visual-basic"></a>Zmienne w Visual Basic
Często należy przechowywać wartości podczas wykonywania obliczeń z Visual Basic. Na przykład możesz chcieć obliczyć kilka wartości, porównać je i wykonywać na nich różne operacje, w zależności od wyniku porównania. Należy zachować wartości, jeśli chcesz je porównać.  
  
## <a name="usage"></a>Użycie  
 Visual Basic, podobnie jak większość języków programowania, używa zmiennych do przechowywania wartości. *Zmienna* ma nazwę (wyraz używany do odwoływania się do wartości, która zawiera zmienna). Zmienna ma również typ danych (który określa rodzaj danych, które mogą być przechowywane w zmiennej). Zmienna może reprezentować tablicę, jeśli musi przechowywać indeksowany zestaw ściśle powiązanych elementów danych.  
  
 Wnioskowanie o typie lokalnym umożliwia deklarowanie zmiennych bez jawnego określenia typu danych. Zamiast tego, kompilator wnioskuje typ zmiennej z typu wyrażenia inicjowania. Aby uzyskać więcej informacji, zobacz [lokalne wnioskowanie o typie](local-type-inference.md) i [zestawienie opcji](../../../language-reference/statements/option-infer-statement.md).  
  
## <a name="assigning-values"></a>Przypisywanie wartości  
 Instrukcje przypisania służą do wykonywania obliczeń i przypisywania wyniku do zmiennej, jak pokazano w poniższym przykładzie.  
  
 [!code-vb[VbVbalrVariables#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrVariables/VB/Class1.vb#1)]  
  
> [!NOTE]
> Znak równości ( `=` ) w tym przykładzie jest operatorem przypisania, a nie operatorem równości. Wartość jest przypisana do zmiennej `applesSold` .  
  
 Aby uzyskać więcej informacji, zobacz [How to: przenoszenie danych do zmiennej i z niej](how-to-move-data-into-and-out-of-a-variable.md).  
  
## <a name="variables-and-properties"></a>Zmienne i właściwości  
 Podobnie jak zmienna, *Właściwość* reprezentuje wartość, do której można uzyskać dostęp. Jest to jednak bardziej złożone niż zmienna. Właściwość używa bloków kodu, które kontrolują sposób ustawiania i pobierania jego wartości. Aby uzyskać więcej informacji, zobacz [różnice między właściwościami i zmiennymi w Visual Basic](../procedures/differences-between-properties-and-variables.md).  
  
## <a name="see-also"></a>Zobacz też

- [Deklaracja zmiennej](variable-declaration.md)
- [Zmienne obiektów](object-variables.md)
- [Rozwiązywanie problemów związanych ze zmiennymi](troubleshooting-variables.md)
- [Porady: przenoszenie danych do zmiennej i z niej](how-to-move-data-into-and-out-of-a-variable.md)
- [Różnice pomiędzy właściwościami i zmiennymi w Visual Basic](../procedures/differences-between-properties-and-variables.md)
- [Wnioskowanie o typie lokalnym](local-type-inference.md)
