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
ms.openlocfilehash: aa045dd5454819a37ad81c76d97fd3e61e7d0420
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58841290"
---
# <a name="auto-implemented-properties-visual-basic"></a>Właściwości zaimplementowane automatycznie (Visual Basic)
*Właściwości zaimplementowane automatycznie* umożliwiają szybko określić właściwość klasy bez konieczności pisania kodu w celu `Get` i `Set` właściwości. Podczas pisania kodu dotyczący automatycznie implementowanej właściwości, kompilator Visual Basic automatycznie tworzy pole prywatne do przechowania zmiennej właściwość, oprócz tworzenia skojarzonego `Get` i `Set` procedur.  
  
 Przy użyciu automatycznie implementowanych właściwości właściwość, łącznie z wartości domyślnej, może być zadeklarowana w jednym wierszu. Poniższy przykład przedstawia trzy deklaracje właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#1)]  
  
 Automatycznie implementowana właściwość jest równoważna z właściwością, dla których wartość właściwości jest przechowywana w pole prywatne. Poniższy przykład kodu pokazuje właściwości zaimplementowane automatycznie.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#5)]  
  
 Poniższy przykład kodu pokazuje równoważny kod w poprzednim przykładzie automatycznie implementowanej właściwości.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#2)]  
  
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
  
 Jak pokazano w przykładzie można przypisać właściwości za pomocą wyrażenia inicjowania lub można przypisać do właściwości w Konstruktorze typu zawierającego.  Można przypisać do pól zapasowy właściwości tylko do odczytu w dowolnym momencie.  
  
## <a name="backing-field"></a>Pole pomocnicze  
 Kiedy Deklarujesz automatycznie implementowana właściwość, Visual Basic automatycznie tworzy ukryte pola prywatnego o nazwie *pole zapasowe* zawiera wartość właściwości. Nazwa pola zapasowego jest nazwą właściwości zaimplementowane automatycznie, poprzedzonej znakiem podkreślenia (_). Na przykład, jeśli zadeklarować automatycznie implementowana właściwość o nazwie `ID`, nosi nazwę pola pomocniczego `_ID`. Jeśli dołączysz składowej klasy, która jest również określany `_ID`, zostanie wyświetlony konflikt nazw i Visual Basic zgłasza błąd kompilatora.  
  
 Pole zapasowe ma również następujące cechy:  
  
-   Modyfikator dostępu dla pola pomocniczego jest zawsze `Private`nawet wtedy, gdy samej właściwości ma poziom dostępu do różnych, takich jak `Public`.  
  
-   Jeśli właściwość jest oznaczona jako `Shared`, pole zapasowe również jest udostępniony.  
  
-   Atrybuty określone dla właściwości nie dotyczą pola pomocniczego.  
  
-   Pole zapasowe jest możliwy z kodu w klasie i narzędzia debugowania, takich jak okna czujki. Jednak pole zapasowe nie są wyświetlane na liście uzupełniania IntelliSense programu word.  
  
## <a name="initializing-an-auto-implemented-property"></a>Inicjowanie automatycznie implementowana właściwość  
 Dowolne wyrażenie, który może służyć do inicjowania pola jest prawidłowy dla automatycznie implementowanej właściwości inicjowania. Podczas inicjowania automatycznie implementowana właściwość wyrażenie jest obliczane i przekazywane do `Set` procedury dla właściwości. W poniższych przykładach kodu pokazano niektóre automatycznie implementowanych właściwości, które zawierają wartości początkowe.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#3)]  
  
 Nie można zainicjować automatycznie implementowana właściwość, która jest elementem członkowskim `Interface`, czy taki, który jest oznaczony jako `MustOverride`.  
  
 Kiedy Deklarujesz automatycznie implementowana właściwość jako członek `Structure`, automatycznie implementowanej właściwości można zainicjować tylko, jeśli jest oznaczony jako `Shared`.  
  
 Kiedy Deklarujesz automatycznie implementowanej właściwości w postaci tablicy, nie można określić granice tablicy jawnego. Jednakże można podać wartość za pomocą inicjatora tablicy, jak pokazano w poniższych przykładach.  
  
 [!code-vb[VbVbalrAutoImplementedProperties#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvbalrautoimplementedproperties/vb/module1.vb#4)]  
  
## <a name="property-definitions-that-require-standard-syntax"></a>Definicje właściwości, które wymagają standardowej składni  
 Właściwości zaimplementowane automatycznie to wygodne, które obsługują wiele scenariuszy programowania. Istnieją jednak sytuacje, w których nie można używać właściwości zaimplementowane automatycznie i zamiast tego należy użyć wzorca, lub *rozwinięte*, składnia właściwości.  
  
 Należy użyć składni definicji właściwości rozszerzonej, jeśli chcesz wykonać jedną z następujących czynności:  
  
-   Dodaj kod, aby `Get` lub `Set` procedury właściwości, takie jak kod do sprawdzania poprawności wartości przychodzących w `Set` procedury. Na przykład możesz chcieć sprawdzić, czy ciąg, który reprezentuje numer telefonu zawiera wymaganą liczbę cyfr, przed ustawieniem właściwości.  
  
-   Określ inną ułatwienia dostępu dla `Get` i `Set` procedury. Na przykład możesz chcieć wprowadzić `Set` procedury `Private` i `Get` procedury `Public`.  
  
-   Tworzenie właściwości, które są `WriteOnly`.  
  
-   Korzystanie z właściwości sparametryzowane (w tym `Default` właściwości). Należy zadeklarować właściwość rozszerzona w celu określenia parametru dla właściwości lub wymagają podania dodatkowych parametrów dla `Set` procedury.  
  
-   Umieść atrybut na pole zapasowe lub zmień poziom dostępu do pola pomocniczego.  
  
-   Podaj komentarze XML dla pola pomocniczego.  
  
## <a name="expanding-an-auto-implemented-property"></a>Rozszerzanie właściwości zaimplementowane automatycznie  
 Jeśli trzeba przekonwertować automatycznie implementowana właściwość rozszerzona właściwość, która zawiera `Get` lub `Set` procedury, Edytor kodu Visual Basic automatycznie wygenerować `Get` i `Set` procedur i `End Property`instrukcji dla właściwości. Kod jest generowany, jeżeli umieścisz kursor w następującym pustym wierszu `Property` instrukcji, wpisz `G` (dla `Get`) lub `S` (dla `Set`) i naciśnij klawisz ENTER. Edytor kodu Visual Basic automatycznie generuje `Get` lub `Set` procedury dla właściwości tylko do odczytu i tylko do zapisu, po naciśnięciu klawisza ENTER na końcu `Property` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Deklarowanie i wywoływanie w właściwości domyślnej w języku Visual Basic](./how-to-declare-and-call-a-default-property.md)
- [Instrukcje: Deklarowanie właściwości z mieszanymi poziomami dostępu](./how-to-declare-a-property-with-mixed-access-levels.md)
- [Instrukcja Property](../../../../visual-basic/language-reference/statements/property-statement.md)
- [ReadOnly](../../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../../visual-basic/language-reference/modifiers/writeonly.md)
- [Obiekty i klasy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
