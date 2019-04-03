---
title: 'Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: b10876c22d2f6dd5832baa0d498db7c4205a3fcb
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2019
ms.locfileid: "58816294"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)
Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżką kwalifikacji kilka metod i właściwości, można przyspieszyć swój kod, powtarzając nie ścieżką kwantyfikacji.  
  
 Istnieją dwa sposoby, można uniknąć powtarzania ścieżką kwantyfikacji. Obiekt można przypisać do zmiennej lub może używać go w `With`... `End With` bloku.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie, przypisując go do zmiennej  
  
1.  Zadeklaruj zmienną typu obiektu, którego uzyskujesz dostęp do często. Określ ścieżkę kwalifikacji w inicjowania część deklaracji.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Dostęp do elementów członkowskich obiektu za pomocą zmiennej.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie korzystając z... Blok końcowy z  
  
1.  Umieść ścieżką kwantyfikacji w `With` instrukcji.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Dostęp do członków obiektu wewnątrz `With` block przed `End With` instrukcji.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
