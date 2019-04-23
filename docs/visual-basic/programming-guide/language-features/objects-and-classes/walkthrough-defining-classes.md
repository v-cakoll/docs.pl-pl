---
title: Definiowanie klas (Visual Basic)
ms.date: 07/20/2015
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
ms.openlocfilehash: 3129824f6e4047420c422503cc366a1c8d28b7e7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59326219"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Przewodnik: Definiowanie klas (Visual Basic)

W tym instruktażu przedstawiono sposób definiowania klas, które można następnie wykorzystać do tworzenia obiektów. Ponadto dowiesz się, jak dodać właściwości i metod do nowej klasy i pokazuje, jak można zainicjować obiektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Aby zdefiniować klasę
  
1. Utwórz projekt, klikając **nowy projekt** na **pliku** menu. **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz aplikację Windows z listy szablonów projektu języka Visual Basic, aby wyświetlić nowy projekt.  
  
3. Dodaj nową klasę do projektu, klikając pozycję **Dodaj klasę** na **projektu** menu. **Dodaj nowy element** pojawi się okno dialogowe.  
  
4. Wybierz **klasy** szablonu.  
  
5. Nadaj nowej klasie `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** Aby wyświetlić kod dla nowej klasy.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    >  Visual Basic można użyć **Edytor kodu** Aby dodać klasę do formularza uruchamiania, wpisując `Class` następuje nazwa nowej klasy, słowo kluczowe. **Edytor kodu** zapewnia odpowiedni `End Class` instrukcji dla Ciebie.  
  
6. Zdefiniuj prywatnego pola do klasy, dodając następujący kod między `Class` i `End Class` instrukcji:  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarowanie pola jako `Private` oznacza może być używany tylko w klasie. Możesz udostępnić pola z poza klasy za pomocą modyfikatorów dostępu, takich jak `Public` dostarczające większy dostęp. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Zdefiniuj właściwość klasy, dodając następujący kod:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Zdefiniuj metodę dla klasy, dodając następujący kod:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Zdefiniuj sparametryzowania konstruktora dla nowej klasy, dodając procedurę o nazwie `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Konstruktor jest wywoływana automatycznie, gdy tworzony jest obiekt na podstawie tej klasy. Ten konstruktor określa wartości pola, który zawiera nazwę użytkownika.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Aby utworzyć przycisk do przetestowania klasy
  
1. Zmień formularz początkowy do trybu projektowania, klikając prawym przyciskiem myszy jej nazwę w **Eksploratora rozwiązań** , a następnie klikając polecenie **Projektant widoków**. Domyślnie formularz początkowy dla projektów aplikacji Windows nazwie Form1.vb. Następnie zostanie wyświetlony formularz główny.  
  
2. Dodawanie przycisku do formularza głównego i go dwukrotnie, aby wyświetlić kod `Button1_Click` programu obsługi zdarzeń. Dodaj następujący kod, aby wywołać procedurę testu:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Aby uruchomić aplikację
  
1. Uruchom aplikację, naciskając klawisz F5. Kliknij przycisk na formularzu, aby wywołać procedurę testu. Wyświetla komunikat informujący, że oryginalna `UserName` jest "MOORE, DOMINIKA", ponieważ wywołana procedura `Capitalize` metody obiektu.  
  
2. Kliknij przycisk **OK** aby odrzucić okno komunikatu. `Button1 Click` Procedury zmienia wartość `UserName` właściwości i wyświetla komunikat informujący, że nowa wartość `UserName` jest "Worden, Jan".  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
