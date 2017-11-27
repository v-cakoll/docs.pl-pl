---
title: Definiowanie klas (Visual Basic)
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- execution [Visual Basic], ending
- objects [Visual Basic], initializing
- Initialize event [Visual Basic]
- files [Visual Basic], closing
- programs [Visual Basic], quitting
- code, exiting
- objects [Visual Basic], creating
- program termination
- classes [Visual Basic], walkthroughs
- class modules, walkthroughs
- Terminate event [Visual Basic]
- execution [Visual Basic], stopping
ms.assetid: 07018828-2d49-4cf5-a44b-19fb15d9efea
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: ec002e1709fa5fe31dfe7744fb91a230c32337a6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Wskazówki: definiowanie klas (Visual Basic)
W tym przewodniku pokazano, jak zdefiniować klasy, które następnie służy do tworzenia obiektów. Ponadto przedstawiono sposób dodawania właściwości i metod do nowej klasy, a demonstruje sposób inicjowania obiektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-a-class"></a>Aby zdefiniować klasę  
  
1.  Tworzenie projektu, klikając **nowy projekt** na **pliku** menu. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz z listy aplikacji systemu Windows [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] szablony, aby wyświetlić nowy projekt projektu.  
  
3.  Dodaj nową klasę w projekcie, klikając **Dodaj klasę** na **projektu** menu. **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
4.  Wybierz **klasy** szablonu.  
  
5.  Nazwa nowej klasy `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** do wyświetlenia kodu dla nowej klasy.  
  
     [!code-vb[VbVbalrOOP#5](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_1.vb)]  
  
    > [!NOTE]
    >  Można użyć [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] **edytora kodu** Aby dodać klasę do uruchamiania formularza, wpisując `Class` — słowo kluczowe następuje nazwa nowej klasy. **Edytora kodu** zawiera odpowiednią `End Class` instrukcji dla Ciebie.  
  
6.  Zdefiniuj pole prywatne dla klasy przez dodanie poniższego kodu między `Class` i `End Class` instrukcji:  
  
     [!code-vb[VbVbalrOOP#7](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_2.vb)]  
  
     Deklarowanie pole jako `Private` oznacza może być używany tylko w klasie. Można udostępnić pola z poza klasą za pomocą modyfikatorów dostępu, takich jak `Public` które zapewniają więcej dostęp. Aby uzyskać więcej informacji, zobacz [poziomy w języku Visual Basic dostępu](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Definiuje właściwości dla klasy przez dodanie poniższego kodu:  
  
     [!code-vb[VbVbalrOOP#8](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_3.vb)]  
  
8.  Zdefiniuj metodę w klasie przez dodanie poniższego kodu:  
  
     [!code-vb[VbVbalrOOP#9](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_4.vb)]  
  
9. Zdefiniuj sparametryzowanym konstruktorze dla nowej klasy, dodając procedurę o nazwie `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_5.vb)]  
  
     `Sub New` Konstruktor jest wywoływana automatycznie po utworzeniu obiektu, w oparciu o tę klasę. Ten konstruktor ustawia wartość pola, zawierające nazwę użytkownika.  
  
### <a name="to-create-a-button-to-test-the-class"></a>Aby utworzyć przycisk, aby przetestować klasy  
  
1.  Zmień formularz startowy do trybu projektowania, klikając prawym przyciskiem myszy jego nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Widok projektanta**. Domyślnie formularz startowy projektów aplikacji systemu Windows nosi nazwę Form1.vb. Następnie zostanie wyświetlony formularz główny.  
  
2.  Dodawanie przycisku do formularza głównego, a następnie kliknij dwukrotnie, aby wyświetlić kod `Button1_Click` obsługi zdarzeń. Dodaj następujący kod, aby wywołać procedurę testu:  
  
     [!code-vb[VbVbalrOOP#12](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-defining-classes_6.vb)]  
  
### <a name="to-run-your-application"></a>Do uruchamiania aplikacji  
  
1.  Uruchom aplikację, naciskając klawisz F5. Kliknij przycisk w formularzu do wywołania tej procedury testu. Wyświetla komunikat informujący, że w oryginalnej `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.  
  
2.  Kliknij przycisk **OK** aby zamknąć okno komunikatu. `Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie zorientowane obiektowo](http://msdn.microsoft.com/library/1cf6e655-3f30-45f1-9a5d-4a88ca24a1c2)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
