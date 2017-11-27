---
title: "Zmienne obiektów w Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- object variables [Visual Basic], about object variables
- variables [Visual Basic], object
- objects [Visual Basic], accessing
- object variables [Visual Basic]
ms.assetid: 6169a196-2b13-4ba5-a205-154bc1b87844
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 44689d649a381618e5d6c934deb2b7b9bea463ed
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="object-variables-in-visual-basic"></a>Zmienne obiektów w Visual Basic
Oprócz wartości są przechowywane bezpośrednio, zmienna może odwoływać się do obiektu. Obiekt można przypisać do zmiennej przyczyn przypisać wartości do zmiennej:  
  
-   Nazwa zmiennej jest często krótsze i łatwiejsze do zapamiętania niż Pełna ścieżka metod i właściwości niezbędne dostępu do tego samego obiektu.  
  
-   Używanie zmiennej, która odwołuje się do obiektu jest bardziej efektywne niż wielokrotnie podczas uzyskiwania dostępu do obiektu za pomocą niezbędne metody lub właściwości.  
  
-   Możesz zmienić zmiennej, aby odwoływać się do innych obiektów, gdy wykonywany jest kod.  
  
## <a name="making-code-shorter"></a>Tworzenie krótszą kodu  
 Zmienne obiektów służy do skrócenia kod, który trzeba wpisywać. W poniższym przykładzie użyto pełnej ścieżki właściwości i metod dostępu do <xref:System.Windows.Forms.Control> obiektu.  
  
```  
' Assume Me is a valid Form, or replace Me with a valid Form.  
Me.ActiveForm.ActiveControl.Text = "Test"  
Me.ActiveForm.ActiveControl.Location = New Point(100, 100)  
Me.ActiveForm.ActiveControl.Show()  
```  
  
 Możesz skrócić ten kod i przyspieszenia wykonywania, jeśli użyjesz zmiennej obiektu dla formantu. Należy zadeklarować zmienną obiektu o określonej klasy, który chcesz przypisać do niej (`Control` w takim przypadku). Po przypisaniu obiektu do zmiennej można traktować go dokładnie tak samo jak traktować obiektu, do którego odwołuje się. Możesz ustawić lub pobrać właściwości obiektu lub użyć dowolnej z metod. W poniższym przykładzie użyto zmiennej obiektu uprościć kod w poprzednim przykładzie.  
  
```  
Dim ctrlActv As System.Windows.Forms.Control = Me.ActiveForm.ActiveControl  
ctrlActv.Text = "Test"  
ctrlActv.Location = New Point(100, 100)  
ctrlActv.Show()  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Deklaracja zmiennej](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Porady: przyspieszanie dostępu do obiektu z długą ścieżką kwantyfikacji](../../../../visual-basic/programming-guide/language-features/variables/how-to-speed-up-access-to-an-object-with-a-long-qualification-path.md)  
 [Deklaracja zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)  
 [Przypisanie zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-assignment.md)  
 [Wartości zmiennej obiektu](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
