---
title: Definiowanie klas (Visual Basic)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-visual-basic
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
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9fc173ad853755c4b02a13abc0a80229bebffe64
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Wskazówki: definiowanie klas (Visual Basic)

W tym przewodniku pokazano, jak zdefiniować klasy, które następnie służy do tworzenia obiektów. Ponadto przedstawiono sposób dodawania właściwości i metod do nowej klasy, a demonstruje sposób inicjowania obiektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Aby zdefiniować klasę
  
1.  Tworzenie projektu, klikając **nowy projekt** na **pliku** menu. **Nowy projekt** zostanie wyświetlone okno dialogowe.  
  
2.  Wybierz aplikację systemu Windows na liście szablony projektu Visual Basic, aby wyświetlić nowy projekt.  
  
3.  Dodaj nową klasę w projekcie, klikając **Dodaj klasę** na **projektu** menu. **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
4.  Wybierz **klasy** szablonu.  
  
5.  Nazwa nowej klasy `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** do wyświetlenia kodu dla nowej klasy.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Korzystając z języka Visual Basic **edytora kodu** Aby dodać klasę do uruchamiania formularza, wpisując `Class` — słowo kluczowe następuje nazwa nowej klasy. **Edytora kodu** zawiera odpowiednią `End Class` instrukcji dla Ciebie.  
  
6.  Zdefiniuj pole prywatne dla klasy przez dodanie poniższego kodu między `Class` i `End Class` instrukcji:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarowanie pole jako `Private` oznacza może być używany tylko w klasie. Można udostępnić pola z poza klasą za pomocą modyfikatorów dostępu, takich jak `Public` które zapewniają więcej dostęp. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7.  Definiuje właściwości dla klasy przez dodanie poniższego kodu:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8.  Zdefiniuj metodę w klasie przez dodanie poniższego kodu:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Zdefiniuj sparametryzowanym konstruktorze dla nowej klasy, dodając procedurę o nazwie `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Konstruktor jest wywoływana automatycznie po utworzeniu obiektu, w oparciu o tę klasę. Ten konstruktor ustawia wartość pola, zawierające nazwę użytkownika.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Aby utworzyć przycisk, aby przetestować klasy
  
1.  Zmień formularz startowy do trybu projektowania, klikając prawym przyciskiem myszy jego nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Widok projektanta**. Domyślnie formularz startowy projektów aplikacji systemu Windows nosi nazwę Form1.vb. Następnie zostanie wyświetlony formularz główny.  
  
2.  Dodawanie przycisku do formularza głównego, a następnie kliknij dwukrotnie, aby wyświetlić kod `Button1_Click` obsługi zdarzeń. Dodaj następujący kod, aby wywołać procedurę testu:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Do uruchamiania aplikacji
  
1.  Uruchom aplikację, naciskając klawisz F5. Kliknij przycisk w formularzu do wywołania tej procedury testu. Wyświetla komunikat informujący, że w oryginalnej `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.  
  
2.  Kliknij przycisk **OK** aby zamknąć okno komunikatu. `Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".  
  
## <a name="see-also"></a>Zobacz także

[Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)  
[Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)