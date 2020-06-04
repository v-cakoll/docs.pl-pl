---
title: Właściwości zaimplementowane automatycznie
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: d991a385e537c43daeb708e96e712acd92110379
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84403385"
---
# <a name="auto-implemented-properties-visual-basic"></a>Właściwości zaimplementowane automatycznie (Visual Basic)
*Zaimplementowane właściwości* umożliwiają szybkie Określanie właściwości klasy bez konieczności pisania kodu do `Get` i `Set` właściwości. Podczas pisania kodu dla właściwości automatycznej implementacji kompilator Visual Basic automatycznie tworzy pole prywatne do przechowywania zmiennej właściwości oprócz tworzenia skojarzonych `Get` i `Set` procedur.  
  
 Przy użyciu właściwości, które są implementowane przez program, właściwość, w tym wartość domyślną, może być zadeklarowana w jednym wierszu. Poniższy przykład przedstawia trzy deklaracje właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Właściwość zaimplementowana przez funkcję jest równoważna właściwości, dla której wartość właściwości jest przechowywana w polu prywatnym. Poniższy przykład kodu pokazuje właściwość, która jest implementowana.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Poniższy przykład kodu pokazuje odpowiedni kod dla poprzedniego przykładu zaimplementowanej właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
 Poniższy kod przedstawia implementowanie właściwości ReadOnly:  
  
```vb  
Class Customer  
   Public ReadOnly Property Tags As New List(Of String)  
   Public ReadOnly Property Name As String = ""  
   Public ReadOnly Property File As String  
  
   Sub New(file As String)  
      Me.File = file  
   End Sub  
End Class  
```  
  
 Można przypisać do właściwości z wyrażeniami inicjalizacji, jak pokazano w przykładzie, lub można przypisać do właściwości w konstruktorze typu zawierającego.  Można przypisać do pól zapasowych właściwości tylko do odczytu w dowolnym momencie.  
  
## <a name="backing-field"></a>Pole zapasowe  
 W przypadku deklarowania automatycznie zaimplementowanej właściwości Visual Basic automatycznie tworzy ukryte pole prywatne o nazwie *pole zapasowe* , aby zawierało wartość właściwości. Nazwa pola zapasowego jest zaimplementowaną nazwą właściwości, poprzedzoną znakiem podkreślenia (_). Na przykład jeśli zadeklarujesz właściwość, która jest zaimplementowana `ID` , pole zapasowe ma nazwę `_ID` . Jeśli dołączysz element członkowski klasy o nazwie `_ID` , zostanie wygenerowane konflikt nazewnictwa, a Visual Basic zgłasza błąd kompilatora.  
  
 Pole zapasowe ma również następujące cechy:  
  
- Modyfikator dostępu dla pola zapasowego jest zawsze `Private` , nawet jeśli sama właściwość ma inny poziom dostępu, na przykład `Public` .  
  
- Jeśli właściwość jest oznaczona jako `Shared` , pole zapasowe jest również udostępniane.  
  
- Atrybuty określone dla właściwości nie mają zastosowania do pola zapasowego.  
  
- Do pola zapasowego można uzyskać dostęp z kodu w klasie oraz z narzędzi debugowania, takich jak okno wyrażeń kontrolnych. Jednak pole zapasowe nie jest wyświetlane na liście uzupełniania słów IntelliSense.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicjowanie właściwości, która została zaimplementowana  
 Dowolne wyrażenie, które może zostać użyte do zainicjowania pola jest prawidłowe dla inicjowania właściwości, która jest implementowana. Po zainicjowaniu właściwości autozaimplementowane wyrażenie jest oceniane i przenoszone do `Set` procedury dla właściwości. W poniższych przykładach kodu przedstawiono niektóre zaimplementowane właściwości, które zawierają wartości początkowe.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Nie można zainicjować właściwości, która jest zaimplementowana, która jest elementem członkowskim `Interface` lub, który jest oznaczony `MustOverride` .  
  
 W przypadku deklarowania właściwości, która jest zaimplementowana jako element członkowski `Structure` , można zainicjować tylko Właściwość zaimplementowaną, jeśli jest oznaczona jako `Shared` .  
  
 W przypadku deklarowania właściwości, która jest zaimplementowana jako tablica, nie można określić jawnych granic tablicy. Można jednak podać wartość przy użyciu inicjatora tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definicje właściwości, które wymagają standardowej składni  
 Właściwości zaimplementowane przez funkcję są wygodne i obsługują wiele scenariuszy programowania. Istnieją jednak sytuacje, w których nie można użyć właściwości, która jest zaimplementowana, a zamiast tego należy użyć standardowej lub *rozwiniętej*składni właściwości.  
  
 Musisz użyć rozwiniętej składni definicji właściwości, jeśli chcesz wykonać jedną z następujących czynności:  
  
- Dodaj kod do `Get` procedury lub `Set` właściwości, takiej jak kod, aby zweryfikować wartości przychodzące w `Set` procedurze. Na przykład możesz chcieć sprawdzić, czy ciąg reprezentujący numer telefonu zawiera wymaganą liczbę cyfr przed ustawieniem wartości właściwości.  
  
- Określ różne ułatwienia dostępu dla `Get` `Set` procedury i. Na przykład może być konieczne wprowadzenie `Set` procedury `Private` i `Get` procedury `Public` .  
  
- Utwórz właściwości, które są `WriteOnly` .  
  
- Użyj właściwości sparametryzowanych (w tym `Default` Właściwości). Należy zadeklarować rozwiniętą właściwość w celu określenia parametru właściwości lub określić dodatkowe parametry dla `Set` procedury.  
  
- Umieść atrybut w polu zapasowym lub zmień poziom dostępu pola zapasowego.  
  
- Podaj Komentarze XML dla pola zapasowego.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozwijanie właściwości, która jest implementowana  
 Jeśli konieczne jest przekonwertowanie automatycznie zaimplementowanej właściwości na rozwiniętą właściwość, która zawiera `Get` procedurę lub `Set` , edytor kodu Visual Basic może automatycznie generować `Get` `Set` procedury i i `End Property` instrukcje dla właściwości. Kod jest generowany, jeśli umieścisz kursor w pustym wierszu po `Property` instrukcji, wpisz a `G` (dla `Get` ) lub `S` (dla `Set` ) i naciśnij klawisz ENTER. Visual Basic Edytor kodu automatycznie generuje `Get` `Set` procedurę lub dla właściwości tylko do odczytu i tylko do zapisu po naciśnięciu klawisza Enter na końcu `Property` instrukcji.  
  
## <a name="see-also"></a>Zobacz też

- [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Porady: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Property — Instrukcja](../../../language-reference/statements/property-statement.md)
- [Trybie](../../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../../language-reference/modifiers/writeonly.md)
- [Obiekty i klasy](../objects-and-classes/index.md)
