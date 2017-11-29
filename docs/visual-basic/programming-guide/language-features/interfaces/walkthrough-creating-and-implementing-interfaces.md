---
title: "Tworzenie i wdrażanie interfejsów (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- interfaces [Visual Basic], walkthroughs
- interfaces [Visual Basic], testing
- interface implementation [Visual Basic], walkthrough
- interfaces [Visual Basic], creating
ms.assetid: ded82af2-9f52-4232-98ef-fe458180f112
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 08bf6dc7344d4f83c8ab1908fdeb29eb4a53e142
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-creating-and-implementing-interfaces-visual-basic"></a>Wskazówki: tworzenie i wdrażanie interfejsów (Visual Basic)
Interfejsy opisują cechy właściwości, metod i zdarzeń, ale pozostawić szczegóły implementacji do struktury lub klasy.  
  
 W tym przewodniku pokazano, jak deklarowanie i implementuje interfejs.  
  
> [!NOTE]
>  Ten przewodnik nie dostarcza informacji na temat sposobu tworzenia interfejsu użytkownika.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-define-an-interface"></a>Aby zdefiniować — interfejs  
  
1.  Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikacji systemu Windows.  
  
2.  Dodaj nowy moduł do projektu, klikając **Dodawanie modułu** na **projektu** menu.  
  
3.  Nazwa nowego modułu `Module1.vb` i kliknij przycisk **Dodaj**. Zostanie wyświetlony kod nowy moduł.  
  
4.  Zdefiniuj interfejs o nazwie `TestInterface` w `Module1` , wpisując `Interface TestInterface` między `Module` i `End Module` instrukcje, a następnie naciskając klawisz ENTER. **Edytora kodu** wcięć `Interface` — słowo kluczowe i dodaje `End Interface` instrukcji do utworzenia bloku kodu.  
  
5.  Definiowanie właściwości, metody i zdarzenia dla interfejsu przez umieszczenie następujący kod między `Interface` i `End Interface` instrukcji:  
  
     [!code-vb[VbVbalrOOP#98](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_1.vb)]  
  
## <a name="implementation"></a>Implementacja  
 Można zauważyć, że składnia użyć do zadeklarowania elementy członkowskie interfejsu różni się od składnię wykorzystywaną do zadeklarować elementów członkowskich klasy. Ta różnica odzwierciedla fakt, że interfejsy nie mogą zawierać kod implementacji.  
  
#### <a name="to-implement-the-interface"></a>Aby zaimplementować interfejs  
  
1.  Dodaj klasę o nazwie `ImplementationClass` przez dodanie następujących instrukcji `Module1`, po `End Interface` instrukcji ale przed wysłaniem `End Module` instrukcji, a następnie naciskając klawisz ENTER:  
  
     [!code-vb[VbVbalrOOP#99](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_2.vb)]  
  
     Jeśli pracujesz w zintegrowane środowisko programistyczne, **edytora kodu** dostarcza odpowiadającego mu `End Class` instrukcji po naciśnięciu klawisza ENTER.  
  
2.  Dodaj następujące `Implements` instrukcji `ImplementationClass`, które nazwy interfejsu klasy implementuje:  
  
     [!code-vb[VbVbalrOOP#100](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_3.vb)]  
  
     Gdy przedstawione oddzielnie od innych elementów u góry klasy lub struktury, `Implements` instrukcji wskazuje, że klasy lub struktury implementuje interfejs.  
  
     Jeśli pracujesz w zintegrowane środowisko programistyczne, **edytora kodu** implementuje wymagane przez członków klasy `TestInterface` po naciśnięciu klawisza ENTER i następny krok można pominąć.  
  
3.  Jeśli nie działają w ramach zintegrowane środowisko programistyczne, musi implementować członków interfejsu `MyInterface`. Dodaj następujący kod do `ImplementationClass` do zaimplementowania `Event1`, `Method1`, i `Prop1`:  
  
     [!code-vb[VbVbalrOOP#101](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_4.vb)]  
  
     `Implements` Instrukcji nazwy interfejsu i elementu członkowskiego interfejsu implementowana.  
  
4.  Definicja ukończenia `Prop1` przez dodanie pola prywatne do przechowywania wartości właściwości klasy:  
  
     [!code-vb[VbVbalrOOP#102](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_5.vb)]  
  
     Zwraca wartość `pval` z właściwości metoda dostępu get.  
  
     [!code-vb[VbVbalrOOP#103](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_6.vb)]  
  
     Ustaw wartość `pval` we właściwości akcesor zestawu.  
  
     [!code-vb[VbVbalrOOP#104](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_7.vb)]  
  
5.  Definicja ukończenia `Method1` przez dodanie poniższego kodu.  
  
     [!code-vb[VbVbalrOOP#105](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_8.vb)]  
  
#### <a name="to-test-the-implementation-of-the-interface"></a>Aby przetestować implementacja interfejsu  
  
1.  Kliknij prawym przyciskiem myszy formularz startowy projektu w **Eksploratora rozwiązań**i kliknij przycisk **kod widoku**. Edytor wyświetla klasy formularza uruchamiania. Domyślnie nazywa się formularz startowy `Form1`.  
  
2.  Dodaj następujące `testInstance` do `Form1` klasy:  
  
     [!code-vb[VbVbalrOOP#120](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_9.vb)]  
  
     Przez zadeklarowanie `testInstance` jako `WithEvents`, `Form1` klasa może obsłużyć jego zdarzenia.  
  
3.  Dodaj następujące obsługi zdarzeń do `Form1` klasy do obsługi zdarzenia generowane przez `testInstance`:  
  
     [!code-vb[VbVbalrOOP#106](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_10.vb)]  
  
4.  Dodaj procedurę o nazwie `Test` do `Form1` klasy do przetestowania klasa implementacji:  
  
     [!code-vb[VbVbalrOOP#107](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_11.vb)]  
  
     `Test` Procedura powoduje utworzenie wystąpienia klasy, która implementuje `MyInterface`, przypisuje to wystąpienie do `testInstance` pola, ustawia właściwość i uruchamia metody za pomocą interfejsu.  
  
5.  Dodaj kod, aby wywołać `Test` procedury z `Form1 Load` procedury uruchamiania formularza:  
  
     [!code-vb[VbVbalrOOP#108](../../../../visual-basic/misc/codesnippet/VisualBasic/walkthrough-creating-and-implementing-interfaces_12.vb)]  
  
6.  Uruchom `Test` procedury, naciskając klawisz F5. Zostanie wyświetlony komunikat "Prop1 ustawiono 9". Po kliknięciu przycisku OK komunikat "Parametr X metoda1 wynosi 5" są wyświetlane. Kliknij przycisk OK, zostanie wyświetlony komunikat "zdarzenia przechwycono programu obsługi zdarzeń".  
  
## <a name="see-also"></a>Zobacz też  
 [Implements — instrukcja](../../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interfejsy](../../../../visual-basic/programming-guide/language-features/interfaces/index.md)  
 [Interface — instrukcja](../../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Event — instrukcja](../../../../visual-basic/language-reference/statements/event-statement.md)
