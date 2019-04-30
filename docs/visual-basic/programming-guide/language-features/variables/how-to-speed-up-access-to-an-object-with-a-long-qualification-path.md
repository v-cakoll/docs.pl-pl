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
ms.openlocfilehash: 94c838a69aab9fcae9dc0c79b6038ee90e2369e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769047"
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Instrukcje: Przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)
Jeśli często uzyskujesz dostęp do obiektu, który wymaga ścieżką kwalifikacji kilka metod i właściwości, można przyspieszyć swój kod, powtarzając nie ścieżką kwantyfikacji.  
  
 Istnieją dwa sposoby, można uniknąć powtarzania ścieżką kwantyfikacji. Obiekt można przypisać do zmiennej lub może używać go w `With`... `End With` bloku.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie, przypisując go do zmiennej  
  
1. Zadeklaruj zmienną typu obiektu, którego uzyskujesz dostęp do często. Określ ścieżkę kwalifikacji w inicjowania część deklaracji.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2. Dostęp do elementów członkowskich obiektu za pomocą zmiennej.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Aby przyspieszyć dostęp do obiektów kwalifikowaną silnie korzystając z... Blok końcowy z  
  
1. Umieść ścieżką kwantyfikacji w `With` instrukcji.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2. Dostęp do członków obiektu wewnątrz `With` block przed `End With` instrukcji.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Zobacz także

- [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
