---
title: "Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic], accessing
- variables [Visual Basic], object
- With statement [Visual Basic]
- With block
- object variables [Visual Basic], accessing
ms.assetid: 3eb7657f-c9fe-4e05-8bc3-4bb14d5ae585
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5d91eeaeb034a4c8b4fefcffdf2fdebe72127d66
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Z... End With — instrukcja](../../../../visual-basic/language-reference/statements/with-end-with-statement.md)
