---
title: 'Przewodnik: Wdrażanie dziedziczenia z obiektami COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 0b3977e73e3b2aa9e80e2dab08d15035283b8387
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62022327"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Przewodnik: Wdrażanie dziedziczenia z obiektami COM (Visual Basic)
Utworzeniu klasy pochodnej klasy Visual Basic z `Public` klas obiektów COM, nawet te, utworzone we wcześniejszych wersjach programu Visual Basic. Właściwości i metody klasy dziedziczone z obiektów COM mogą być zastąpione lub przeciążone, podobnie jak właściwości i metody inne klasy bazowej można zastąpić lub przeciążone. Dziedziczenie z obiektami COM jest przydatne, jeśli masz istniejące biblioteki klas, które nie chcesz ponownie skompilować.  
  
 Poniższa procedura pokazuje, jak używać języka Visual Basic 6.0 do tworzenia obiektów COM, który zawiera klasę, a następnie użyć go jako klasę bazową.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Aby zbudować obiekt COM, który jest używany w tym przewodniku  
  
1. W Visual Basic 6.0 otwórz nowy projekt ActiveX DLL. Projekt o nazwie `Project1` zostanie utworzony. Ma ona klasę o nazwie `Class1`.  
  
2. W **Eksplorator projektów**, kliknij prawym przyciskiem myszy **projektu Project1**, a następnie kliknij przycisk **właściwości projektu Project1**. **Właściwości projektu** zostanie wyświetlone okno dialogowe.  
  
3. Na **ogólne** karcie **właściwości projektu** okno dialogowe Zmień nazwę projektu, wpisując `ComObject1` w **Nazwa projektu** pola.  
  
4. W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `Class1`, a następnie kliknij przycisk **właściwości**. **Właściwości** zostanie wyświetlone okno dla tej klasy.  
  
5. Zmiana `Name` właściwość `MathFunctions`.  
  
6. W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `MathFunctions`, a następnie kliknij przycisk **Wyświetl kod**. **Edytor kodu** jest wyświetlana.  
  
7. Dodaj zmienną lokalną, do przechowywania wartości właściwości:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8. Dodaj właściwość `Let` i właściwość `Get` procedury właściwości:  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. Dodawanie funkcji:  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Utwórz i zarejestruj obiekt COM, klikając **wprowadzić ComObject1.dll** na **pliku** menu.  
  
    > [!NOTE]
    >  Chociaż można także udostępnić klasy utworzonej za pomocą Visual Basic jako obiekt COM, nie jest obiektem COM wartość true, a nie może być używana w tym przewodniku. Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjne  
 W poniższej procedurze utworzysz zestawu międzyoperacyjnego, który działa jako Most między kodem niezarządzanym (np. obiekt COM) i kod zarządzany, który korzysta z programu Visual Studio. Zestawu międzyoperacyjnego, który tworzy języka Visual Basic obsługuje wiele szczegółów pracy z obiektami COM, takich jak *marshaling międzyoperacyjny*, proces tworzenia pakietów parametrów i zwracanych wartości danych równoważne typy przechodzące do a obiekty COM. W aplikacji Visual Basic wskazuje odwołanie do zestawu międzyoperacyjnego nie rzeczywistego obiektu COM.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Obiekt COM za pomocą programu Visual Basic 2005 i nowszych wersjach  
  
1. Otwórz nowy projekt aplikacji Windows Visual Basic.  
  
2. Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
3. Na **COM** kartę, kliknij dwukrotnie `ComObject1` w **nazwa składnika** listy, a następnie kliknij przycisk **OK**.  
  
4. Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
5. W **szablony** okienku kliknij **klasy**.  
  
     Domyślna nazwa pliku `Class1.vb`, pojawia się w **nazwa** pola. Zmień to pole na MathClass.vb, a następnie kliknij przycisk **Dodaj**. Spowoduje to utworzenie klasę o nazwie `MathClass`i wyświetla jego kod.  
  
6. Dodaj następujący kod na górze `MathClass` dziedziczyć z klasy COM.  
  
     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]  
  
7. Przeciążenia metody publiczne klasy bazowej, dodając następujący kod do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]  
  
8. Rozszerzanie odziedziczoną klasę, dodając następujący kod do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]  
  
 Nowa klasa dziedziczy właściwości klasy bazowej w obiekcie COM, przeciążenia metody i definiuje nową metodę rozszerzenia klasy.  
  
#### <a name="to-test-the-inherited-class"></a>Aby przetestować odziedziczoną klasę  
  
1. Dodawanie przycisku do uruchamiania formularza, a następnie go dwukrotnie, aby wyświetlić jej kod.  
  
2. W przycisku `Click` procedury obsługi zdarzeń, Dodaj następujący kod, aby utworzyć wystąpienie `MathClass` i wywołania przeciążonych metod:  
  
     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]  
  
3. Uruchom projekt, naciskając klawisz F5.  
  
 Po kliknięciu przycisku w formularzu `AddNumbers` metoda najpierw jest wywoływana z `Short` liczb, typ danych i Visual Basic wybiera odpowiednią metodę z klasy bazowej. Drugie wywołanie `AddNumbers` zostaje skierowany do przeciążenia metody z `MathClass`. Trzecie wywołanie wywołania `SubtractNumbers` metody, która rozszerza klasę. Ustawiono właściwość w klasie bazowej, a wartość jest wyświetlana.  
  
## <a name="next-steps"></a>Następne kroki  
 Być może zauważono, że przeciążone `AddNumbers` funkcja wydaje się mieć taki sam typ jako metody dziedziczone z klasy bazowej obiektu COM danych. Jest to spowodowane argumentów i parametrów metody klasy bazowej są definiowane jako 16-bitowych liczb całkowitych w języku Visual Basic 6.0, ale są one widoczne jako 16-bitowych liczb całkowitych typu `Short` w nowszych wersjach programu Visual Basic. Nowa funkcja akceptuje 32-bitowych liczb całkowitych i przeciążenia funkcji klasy bazowej.  
  
 Podczas pracy z obiektami COM, upewnij się, że należy sprawdzić, rozmiar i typy danych parametrów. Na przykład korzystając z obiektu COM, który akceptuje jako argument obiektu kolekcji Visual Basic 6.0, nie może dostarczyć kolekcji z nowszej wersji programu Visual Basic.  
  
 Właściwości i metody dziedziczone z klasy COM można przesłonić, co oznacza, że można zadeklarować lokalnego właściwości lub metody, która zastępuje właściwość lub dziedziczone z klasy bazowej COM. Reguły zastępowania dziedziczonych właściwości modelu COM są podobne do reguł zastępowanie innych właściwości i metod z następującymi wyjątkami:  
  
- Jeśli zastąpisz każda właściwość lub metoda odziedziczoną z klasy COM muszą przesłaniać wszystkie odziedziczone właściwości i metody.  
  
- Właściwości, które używają `ByRef` parametrów nie może być zastąpiona.  
  
## <a name="see-also"></a>Zobacz także

- [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
