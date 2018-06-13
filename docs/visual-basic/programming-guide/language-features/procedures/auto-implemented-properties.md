---
title: Właściwości zaimplementowane automatycznie (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AutoProperty
- vb.AutoImplementedProperty
helpviewer_keywords:
- properties [Visual Basic], auto-implemented
- properties [Visual Basic], auto-implemented
- auto-implemented properties [Visual Basic]
ms.assetid: 5c669f0b-cf95-4b4e-ae84-9cc55212ca87
ms.openlocfilehash: bc83163a024bd50d3e256b4eb49861669f8c02c3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33656334"
---
# <a name="auto-implemented-properties-visual-basic"></a>Właściwości zaimplementowane automatycznie (Visual Basic)
*Właściwości zaimplementowane automatycznie* można szybko określić właściwość klasy bez konieczności pisania kodu do `Get` i `Set` właściwości. Podczas pisania kodu dla właściwości zaimplementowane automatycznie kompilator Visual Basic automatycznie tworzy pole prywatne do przechowywania zmiennej właściwość oprócz tworzenia skojarzony `Get` i `Set` procedur.  
  
 Właściwości zaimplementowane automatycznie właściwości, łącznie z wartości domyślnej, mogą być deklarowane w jednym wierszu. W poniższym przykładzie przedstawiono trzy deklaracje właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](./codesnippet/VisualBasic/auto-implemented-properties_1.vb)]  
  
 Właściwości zaimplementowane automatycznie odpowiada właściwości, dla których wartość właściwości jest przechowywana w pole prywatne. Poniższy przykład kodu pokazuje właściwości zaimplementowane automatycznie.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](./codesnippet/VisualBasic/auto-implemented-properties_2.vb)]  
  
 Poniższy przykład kodu zawiera kod odpowiednik w poprzednim przykładzie automatycznie implementowanej właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](./codesnippet/VisualBasic/auto-implemented-properties_3.vb)]  
  
 Poniższy kod Pokaż Implementowanie właściwości tylko do odczytu:  
  
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
  
 Jak pokazano w przykładzie można przypisać do właściwości, za pomocą wyrażeń inicjowania lub można przypisać do właściwości w Konstruktorze typu zawierającego.  W dowolnym momencie można przypisać do pola zapasowy właściwości tylko do odczytu.  
  
## <a name="backing-field"></a>Pola zapasowego  
 Właściwości zaimplementowane automatycznie w deklaracji, Visual Basic automatycznie tworzy ukryte pole prywatnej o nazwie *pole zapasowe* zawiera wartość właściwości. Nazwa pola zapasowego jest nazwa właściwości zaimplementowane automatycznie poprzedzone znaku podkreślenia (_). Na przykład, jeśli zadeklarować automatycznie implementowana właściwość o nazwie `ID`, nosi nazwę pola zapasowego `_ID`. Jeśli dołączysz element członkowski klasy o nazwie `_ID`, tworzy konflikt nazw i Visual Basic zgłasza błąd kompilatora.  
  
 Pole zapasowe ma również następujące cechy:  
  
-   Modyfikator dostępu do pola zapasowego jest zawsze `Private`nawet wtedy, gdy samej właściwości ma poziom dostępu do innego, takich jak `Public`.  
  
-   Jeśli właściwość jest oznaczona jako `Shared`, pole zapasowe również jest udostępnione.  
  
-   Pole zapasowe nie dotyczą atrybutów określonych dla właściwości.  
  
-   Pole zapasowe są dostępne z kodu w klasie i debugowania narzędzi, takich jak okna czujki. Pole zapasowe nie są wyświetlane na liście uzupełniania IntelliSense programu word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicjowanie właściwości zaimplementowane automatycznie  
 Dowolne wyrażenie, który może służyć do zainicjowania pola jest prawidłowa dla automatycznie implementowanej właściwości inicjowania. Podczas inicjowania właściwości zaimplementowane automatycznie wyrażenie jest obliczane i przekazane do `Set` procedury dla właściwości. W poniższych przykładach kodu pokazano niektóre automatycznie implementowane właściwości, które obejmują wartości początkowe.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](./codesnippet/VisualBasic/auto-implemented-properties_4.vb)]  
  
 Nie można zainicjować automatycznie implementowana właściwość, która jest elementem członkowskim `Interface`, lub oznaczona `MustOverride`.  
  
 Gdy zadeklarować właściwości zaimplementowane automatycznie jako element członkowski `Structure`, automatycznie implementowane właściwości można zainicjować tylko, jeśli jest oznaczony jako `Shared`.  
  
 Przy deklarowaniu automatycznie implementowanej właściwości w postaci tablicy nie można określić granice tablicy jawnego. Jednak można podać wartość za pomocą inicjatora tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](./codesnippet/VisualBasic/auto-implemented-properties_5.vb)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definicje właściwości, które wymagają standardowej składni  
 Właściwości zaimplementowane automatycznie wygodne i obsługuje wiele scenariuszy programowania. Istnieją jednak sytuacji, w których nie można używać właściwości zaimplementowane automatycznie i zamiast tego należy użyć standard, lub *rozwinięty*, składni właściwości.  
  
 Należy użyć składni definicji właściwości rozszerzonej, jeśli chcesz wykonać jedną z następujących czynności:  
  
-   Dodaj kod, aby `Get` lub `Set` procedury właściwości, takie jak kod do sprawdzania poprawności wartości przychodzących w `Set` procedury. Na przykład można sprawdzić, czy ciąg reprezentujący numer telefonu zawiera wymaganą liczbę cyfr przed ustawieniem wartości właściwości.  
  
-   Określ inną ułatwień dostępu dla `Get` i `Set` procedury. Na przykład można wprowadzić `Set` procedury `Private` i `Get` procedury `Public`.  
  
-   Utworzenie właściwości, które są `WriteOnly`.  
  
-   Użyj właściwości parametrycznego (w tym `Default` właściwości). Musisz zadeklarować rozszerzonych właściwości w celu określenia parametru dla właściwości lub wymagają podania dodatkowych parametrów dla `Set` procedury.  
  
-   Umieść atrybut na pole zapasowe lub zmień poziom dostępu pola zapasowego.  
  
-   Podaj komentarze XML dla pola zapasowego.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozszerzanie właściwości zaimplementowane automatycznie  
 Jeśli trzeba przekonwertować automatycznie implementowanej właściwości rozszerzonych właściwości, który zawiera `Get` lub `Set` procedury edytora kodu języka Visual Basic może automatycznie generować `Get` i `Set` procedury i `End Property`instrukcji dla właściwości. Kod jest generowany, gdy kursor zostanie umieszczony na pusty wiersz poniżej `Property` instrukcji, a typ `G` (dla `Get`) lub `S` (dla `Set`) i naciśnij klawisz ENTER. Edytor kodu języka Visual Basic automatycznie generuje `Get` lub `Set` procedury dla właściwości tylko do odczytu i tylko do zapisu, po naciśnięciu klawisza ENTER na końcu `Property` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: deklarowanie i wywoływanie w właściwości domyślnej w Visual Basic](./how-to-declare-and-call-a-default-property.md)  
 [Instrukcje: deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)  
 [Property, instrukcja](../../../../visual-basic/language-reference/statements/property-statement.md)  
 [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)  
 [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)  
 [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
