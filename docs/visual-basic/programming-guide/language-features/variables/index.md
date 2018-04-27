---
title: Zmienne w Visual Basic
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- values [Visual Basic], storing
ms.assetid: 4cfaa06d-4ae3-4307-897b-cf599dc24caa
caps.latest.revision: 27
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5e4397fb90e4fa5a3e68390137b84a375cf35956
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
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
