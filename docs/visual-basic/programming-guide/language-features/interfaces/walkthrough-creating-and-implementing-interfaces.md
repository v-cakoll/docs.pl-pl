---
title: Tworzenie i wdrażanie interfejsów (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
ms.openlocfilehash: faed4d3c9498938e022daf821dd0aefbcbcf2e8d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053772"
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Przewodnik: Tworzenie i wdrażanie interfejsów (Visual Basic)

Interfejsy opisują cechy właściwości, metody i zdarzenia, ale pozostawić szczegółów implementacji do struktury lub klasy.  
  
 W tym instruktażu pokazano, jak zadeklarować i implementuje interfejs.  
  
> [!NOTE]
>  Ten przewodnik nie zawiera informacji o sposobie tworzenia interfejsu użytkownika.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
## <a name="to-define-an-interface"></a>Aby zdefiniować interfejs
  
1. Otwórz nowy projekt aplikacji Windows Visual Basic.  
  
2. Dodaj nowy moduł do projektu, klikając pozycję **Dodawanie modułu** na **projektu** menu.  
  
3. Nazwij nowy moduł `Module1.vb` i kliknij przycisk **Dodaj**. Kod dla nowego modułu jest wyświetlany.  
  
4. Zdefiniuj interfejs o nazwie `TestInterface` w ramach `Module1` , wpisując `Interface TestInterface` między `Module` i `End Module` instrukcji, a następnie naciśnij klawisz ENTER. **Edytor kodu** wcięcia `Interface` — słowo kluczowe i dodaje `End Interface` poufności informacji w celu utworzenia bloku kodu.  
  
5. Definiowanie właściwości, metody i zdarzenia dla interfejsu użytkownika, umieszczając następujący kod między `Interface` i `End Interface` instrukcji:  
  
     [!code-vb[VbVbalrOOP#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#98)]
  
## <a name="implementation"></a>Implementacja

 Można zauważyć, że składnia używane do deklarowania składowych interfejsu różni się od składni używane do deklarowania składowych klasy. Różnica ta odzwierciedla fakt, że interfejsy nie mogą zawierać kod implementacji.  
  
### <a name="to-implement-the-interface"></a>Aby zaimplementować interfejs
  
1. Dodaj klasę o nazwie `ImplementationClass` , dodając następującą instrukcję, aby `Module1`po `End Interface` instrukcji lecz przed `End Module` instrukcji, a następnie naciśnij klawisz ENTER:  
  
     [!code-vb[VbVbalrOOP#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#99)]
  
     Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** dostarcza pasujący obiekt typu `End Class` instrukcji po naciśnięciu klawisza ENTER.  
  
2. Dodaj następujący kod `Implements` instrukcję, aby `ImplementationClass`, który nazwy interfejsu klasy implementuje:  
  
     [!code-vb[VbVbalrOOP#100](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#100)]
  
     Gdy przedstawione oddzielnie od innych elementów w górnej części klasy lub struktury, `Implements` deklaracja wskazuje, że klasa lub struktura implementuje interfejs.  
  
     Jeśli pracujesz w zintegrowanym środowisku programistycznym, **Edytor kodu** implementuje wymagane przez elementy członkowskie klasy `TestInterface` po naciśnięciu klawisza ENTER i można pominąć następny krok.  
  
3. Jeśli nie działają w ramach zintegrowanego środowiska programistycznego, należy zaimplementować wszyscy członkowie interfejsu `MyInterface`. Dodaj następujący kod do `ImplementationClass` do zaimplementowania `Event1`, `Method1`, i `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#101)]
  
     `Implements` Instrukcji nazwy interfejsu i członka interfejsu implementowanego.  
  
4. Definicja ukończenia `Prop1` przez dodanie pola prywatnego do klasy, która jest przechowywana wartość właściwości:  
  
     [!code-vb[VbVbalrOOP#102](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#102)]
  
     Zwraca wartość `pval` z właściwości metoda dostępu get.  
  
     [!code-vb[VbVbalrOOP#103](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#103)]
  
     Ustaw wartość `pval` we właściwości ustawiająca metoda dostępu.  
  
     [!code-vb[VbVbalrOOP#104](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#104)]
  
5. Definicja ukończenia `Method1` , dodając następujący kod.  
  
     [!code-vb[VbVbalrOOP#105](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#105)]
  
### <a name="to-test-the-implementation-of-the-interface"></a>Aby przetestować implementacji interfejsu
  
1. Kliknij prawym przyciskiem myszy formularz początkowy dla projektu w **Eksploratora rozwiązań**i kliknij przycisk **Wyświetl kod**. W edytorze są wyświetlane klasy dla formularza użytkownika uruchamiania. Domyślnie, formularz początkowy jest nazywany `Form1`.  
  
2. Dodaj następujący kod `testInstance` pole `Form1` klasy:  
  
     [!code-vb[VbVbalrOOP#120](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#120)]
  
     DEKLARUJĄC `testInstance` jako `WithEvents`, `Form1` klasy może obsługiwać ze zdarzeniami.  
  
3. Dodaj następującą obsługę zdarzeń w celu `Form1` klasy do obsługi zdarzeń wywołanych przez `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#106)]
  
4. Dodaj procedurę o nazwie `Test` do `Form1` klasy do przetestowania klasy implementacji:  
  
     [!code-vb[VbVbalrOOP#107](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#107)]
  
     `Test` Procedura powoduje utworzenie wystąpienia klasy, która implementuje `MyInterface`, przypisuje tego wystąpienia `testInstance` pole, ustawia właściwość i uruchamia metodę za pośrednictwem interfejsu.  
  
5. Dodaj kod, aby wywołać `Test` procedury z `Form1 Load` procedury uruchamiania formularza:  
  
     [!code-vb[VbVbalrOOP#108](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOOP/VB/OOP.vb#108)]
  
6. Uruchom `Test` procedury, naciskając klawisz F5. Jest wyświetlany komunikat "właściwość1 zostało ustawione na 9". Jest wyświetlany po kliknięciu przycisku OK, komunikat "Parametr X metoda1 wynosi 5". Kliknij przycisk OK, zostanie wyświetlony komunikat "program obsługi zdarzeń przechwycono zdarzenia".  
  
## <a name="see-also"></a>Zobacz także

- [Implements, instrukcja](../../../../visual-basic/language-reference/statements/implements-statement.md)
- [Interfejsy](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Instrukcja Interface](../../../../visual-basic/language-reference/statements/interface-statement.md)
- [Event, instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md)
