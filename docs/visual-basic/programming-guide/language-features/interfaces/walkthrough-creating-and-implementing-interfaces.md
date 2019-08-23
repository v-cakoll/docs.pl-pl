---
title: Tworzenie i implementowanie interfejsów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: 62e301e9eb366d14b58088d3e2cda3b567d17f5b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923308"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Przewodnik: Tworzenie i implementowanie interfejsów (Visual Basic)

Interfejsy opisują właściwości, metody i zdarzenia, ale pozostawiają szczegóły implementacji do struktur lub klas.  
  
 W tym instruktażu pokazano, jak zadeklarować i zaimplementować interfejs.  
  
> [!NOTE]
> Ten Instruktaż nie zawiera informacji o sposobie tworzenia interfejsu użytkownika.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Aby zdefiniować interfejs
  
1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows.  
  
2. Dodaj nowy moduł do projektu, klikając pozycję **Dodaj moduł** w menu **projekt** .  
  
3. Nazwij nowy moduł `Module1.vb` , a następnie kliknij przycisk **Dodaj**. Zostanie wyświetlony kod dla nowego modułu.  
  
4. Zdefiniuj interfejs o nazwie `TestInterface` w `Module1` programie, `Interface TestInterface` wpisując między `Module` instrukcjami `End Module` a i naciskając klawisz ENTER. **Edytor kodu** tworzy wcięcie `Interface` `End Interface` słowa kluczowego i dodaje instrukcję do utworzenia bloku kodu.  
  
5. Zdefiniuj właściwość, metodę i zdarzenie dla interfejsu, umieszczając następujący kod między `Interface` instrukcjami i: `End Interface`  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementacja

 Można zauważyć, że składnia użyta do deklarowania składowych interfejsu różni się od składni używanej do deklarowania elementów członkowskich klasy. Różnica ta odzwierciedla fakt, że interfejsy nie mogą zawierać kodu implementacji.  
  
### <a name="to-implement-the-interface"></a>Aby zaimplementować interfejs
  
1. Dodaj klasę o nazwie `ImplementationClass` przez dodanie następującej instrukcji do `Module1`, po `End Interface` instrukcji, ale przed `End Module` instrukcją, a następnie naciśnij klawisz ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** dostarcza pasujące `End Class` instrukcje po naciśnięciu klawisza ENTER.  
  
2. Dodaj następującą `Implements` instrukcję do `ImplementationClass`, która nazywa interfejs implementujący przez klasę:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Gdy jest wyszczególnione oddzielnie od innych elementów w górnej części klasy lub struktury, `Implements` instrukcja wskazuje, że Klasa lub struktura implementuje interfejs.  
  
     Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** implementuje elementy członkowskie klasy wymagane przez `TestInterface` naciśnięcie klawisza Enter i można pominąć następny krok.  
  
3. Jeśli nie Pracujesz w zintegrowanym środowisku programistycznym, musisz zaimplementować wszystkie elementy członkowskie interfejsu `MyInterface`. Dodaj następujący kod w `ImplementationClass` celu zaimplementowania `Method1` `Event1`, i `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` Instrukcja nazywa interfejs i składową interfejsu, która jest implementowana.  
  
4. Wypełnij definicję `Prop1` przez dodanie pola prywatnego do klasy, która przechowuje wartość właściwości:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Zwróć wartość `pval` z elementu z metody dostępu get właściwości.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Ustaw wartość `pval` w polu akcesor zestawu właściwości.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Wykonaj definicję `Method1` , dodając następujący kod.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Aby przetestować implementację interfejsu
  
1. Kliknij prawym przyciskiem myszy formularz startowy dla projektu w **Eksplorator rozwiązań**, a następnie kliknij polecenie **Wyświetl kod**. Edytor wyświetla klasę dla formularza startowego. Domyślnie formularz startowy jest wywoływany `Form1`.  
  
2. Dodaj następujące `testInstance` pole `Form1` do klasy:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     Deklarując `testInstance` jako `WithEvents`, Klasamożeobsłużyćswojezdarzenia.`Form1`  
  
3. Dodaj do `Form1` klasy następujący program obsługi zdarzeń, aby obsłużyć zdarzenia `testInstance`zgłoszone przez:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Dodaj podprocedurę o nazwie `Test` `Form1` do klasy w celu przetestowania klasy implementacji:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     Procedura tworzy wystąpienie klasy, która implementuje `MyInterface`, `testInstance` przypisuje to wystąpienie do pola, ustawia właściwość i uruchamia metodę za pomocą interfejsu. `Test`  
  
5. Dodaj kod, aby wywołać `Test` procedurę `Form1 Load` z procedury dotyczącej formularza startowego:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. `Test` Uruchom procedurę, naciskając klawisz F5. Zostanie wyświetlony komunikat "Prop1 został ustawiony na 9". Po kliknięciu przycisku OK zostanie wyświetlony komunikat "parametr X dla Metoda1 jest 5". Kliknij przycisk OK, a zostanie wyświetlony komunikat "procedura obsługi zdarzeń przechwycono zdarzenie".  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Instrukcja Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event, instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md)
