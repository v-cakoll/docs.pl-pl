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
ms.openlocfilehash: 679f4fd55f142c2c4bb63a556feb95c074960b12
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69914732"
---
# <a name="walkthrough-defining-classes-visual-basic"></a>Przewodnik: Definiowanie klas (Visual Basic)

W tym instruktażu pokazano, jak definiować klasy, których można użyć do tworzenia obiektów. Pokazano w nim także, jak dodać właściwości i metody do nowej klasy, i demonstruje sposób inicjowania obiektu.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-a-class"></a>Aby zdefiniować klasę
  
1. Utwórz projekt, klikając pozycję **Nowy projekt** w menu **plik** . **Nowy projekt** pojawi się okno dialogowe.  
  
2. Wybierz pozycję Aplikacja systemu Windows z listy Visual Basic szablonów projektu, aby wyświetlić nowy projekt.  
  
3. Dodaj nową klasę do projektu, klikając pozycję **Dodaj klasę** w menu **projekt** . **Dodaj nowy element** pojawi się okno dialogowe.  
  
4. Wybierz szablon **klasy** .  
  
5. Nazwij nową klasę `UserNameInfo.vb`, a następnie kliknij przycisk **Dodaj** , aby wyświetlić kod dla nowej klasy.  
  
     [!code-vb[VbVbalrOOP#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#5)]
  
    > [!NOTE]
    > Aby dodać klasę do formularza startowego, można użyć **edytora kodu** Visual Basic przez wpisanie słowa kluczowego `Class` , po którym następuje nazwa nowej klasy. **Edytor kodu** zawiera odpowiednią `End Class` instrukcję.  
  
6. Zdefiniuj pole prywatne dla klasy, dodając następujący kod między `Class` instrukcjami i: `End Class`  
  
     [!code-vb[VbVbalrOOP#7](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#7)]
  
     Deklarowanie pola jako `Private` oznacza, że może być używane tylko w obrębie klasy. Można udostępnić pola spoza klasy za pomocą modyfikatorów dostępu, takich jak `Public` zapewnianie większej dostępu. Aby uzyskać więcej informacji, zobacz temat [Poziomy dostępu w języku Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).  
  
7. Zdefiniuj właściwość dla klasy, dodając następujący kod:  
  
     [!code-vb[VbVbalrOOP#8](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#8)]
  
8. Zdefiniuj metodę dla klasy, dodając następujący kod:  
  
     [!code-vb[VbVbalrOOP#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#9)]
  
9. Zdefiniuj sparametryzowany Konstruktor dla nowej klasy, dodając procedurę o nazwie `Sub New`:  
  
     [!code-vb[VbVbalrOOP#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#10)]
  
     `Sub New` Konstruktor jest wywoływany automatycznie, gdy tworzony jest obiekt oparty na tej klasie. Ten konstruktor ustawia wartość pola, które zawiera nazwę użytkownika.  
  
## <a name="to-create-a-button-to-test-the-class"></a>Aby utworzyć przycisk służący do testowania klasy
  
1. Aby zmienić formularz startowy na tryb projektowania, kliknij prawym przyciskiem myszy jego nazwę w **Eksplorator rozwiązań** a następnie kliknij pozycję **Projektant widoków**. Domyślnie formularz uruchamiania projektów aplikacji systemu Windows nosi nazwę Form1. vb. Zostanie wyświetlony formularz główny.  
  
2. Dodaj przycisk do formularza głównego i kliknij go dwukrotnie, aby wyświetlić kod dla `Button1_Click` programu obsługi zdarzeń. Dodaj następujący kod, aby wywołać procedurę testową:  
  
     [!code-vb[VbVbalrOOP#12](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#12)]
  
## <a name="to-run-your-application"></a>Aby uruchomić aplikację
  
1. Uruchom aplikację, naciskając klawisz F5. Kliknij przycisk w formularzu, aby wywołać procedurę testową. Wyświetla komunikat informujący o tym, że oryginał `UserName` jest "Moore, Bobby", ponieważ procedura `Capitalize` nazywana jest metodą obiektu.  
  
2. Kliknij przycisk **OK** , aby odrzucić okno komunikatu. Procedura zmienia wartość `UserName` właściwości i wyświetla komunikat informujący `UserName` o tym, że nowa wartość to "Worden, Jan". `Button1 Click`  
  
## <a name="see-also"></a>Zobacz także

- [Programowanie zorientowane obiektowo (Visual Basic)](../../concepts/object-oriented-programming.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
