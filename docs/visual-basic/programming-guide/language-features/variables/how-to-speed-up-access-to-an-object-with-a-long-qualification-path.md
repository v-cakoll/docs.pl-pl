---
title: 'Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
ms.openlocfilehash: d52d13feb0f85065c0623b5937f558b841c036dd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-speed-up-access-to-an-object-with-a-long-qualification-path-visual-basic"></a>Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)
Jeśli często dostępu do obiektu, który wymaga ścieżką kwantyfikacji kilka metod i właściwości można przyspieszyć kodu nie powtarzając ścieżką kwantyfikacji.  
  
 Istnieją dwa sposoby można uniknąć powtarzania ścieżką kwantyfikacji. Obiekt można przypisać do zmiennej lub używania go w `With`... `End With` bloku.  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-assigning-it-to-a-variable"></a>Aby przyspieszyć dostępu do obiektu silnie kwalifikowana przez przypisanie go do zmiennej  
  
1.  Deklarowanie zmiennej typu obiektu, którego uzyskujesz dostęp do często. Określ ścieżkę kwalifikacji w części inicjowania deklaracji.  
  
    ```  
    Dim ctrlActv As Control = someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Dostęp do elementów członkowskich obiektu za pomocą zmiennej.  
  
    ```  
    ctrlActv.Text = "Test"  
    ctrlActv.Location = New Point(100, 100)  
    ctrlActv.Show()  
    ```  
  
### <a name="to-speed-up-access-to-a-heavily-qualified-object-by-using-a-withend-with-block"></a>Aby przyspieszyć dostępu do obiektu silnie kwalifikowanej przy użyciu With... Blok końcowy z  
  
1.  Umieść ścieżką kwantyfikacji w `With` instrukcji.  
  
    ```  
    With someForm.ActiveForm.ActiveControl  
    ```  
  
2.  Dostęp do elementów członkowskich obiektu wewnątrz `With` zablokować przed `End With` instrukcji.  
  
    ```  
        .Text = "Test"  
        .Location = New Point(100, 100)  
        .Show()  
    End With  
    ```  
  
## <a name="see-also"></a>Zobacz też  
 [Zmienne obiektów](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [With...End With, instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
