---
title: 'Przewodnik: Implementowanie dziedziczenia z obiektami COM (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
ms.openlocfilehash: 7cbf71d7a2bbd1e94864e785894fdea41d522486
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71053335"
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Przewodnik: Implementowanie dziedziczenia z obiektami COM (Visual Basic)

Klasy Visual Basic można tworzyć z `Public` klas obiektów com, nawet tych, które zostały utworzone we wcześniejszych wersjach Visual Basic. Właściwości i metody klasy dziedziczone z obiektów COM można przesłaniać lub przeciążać tylko wtedy, gdy właściwości i metody dowolnej innej klasy bazowej mogą zostać zastąpione lub przeciążone. Dziedziczenie z obiektów COM jest przydatne, gdy masz istniejącą bibliotekę klas, której nie chcesz ponownie skompilować.

Poniższa procedura pokazuje, jak używać Visual Basic 6,0 do tworzenia obiektu COM, który zawiera klasę, a następnie używać jej jako klasy bazowej.

[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]

## <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Aby skompilować obiekt COM, który jest używany w tym instruktażu

1. W Visual Basic 6,0 Otwórz nowy projekt biblioteki DLL ActiveX. Projekt o nazwie `Project1` jest tworzony. Ma klasę o nazwie `Class1`.

2. W **Eksploratorze projektów**kliknij prawym przyciskiem myszy pozycję **Project1**, a następnie kliknij pozycję **Właściwości Project1**. Zostanie wyświetlone okno dialogowe **właściwości projektu** .

3. Na karcie **Ogólne** okna dialogowego **właściwości projektu** Zmień nazwę projektu, wpisując `ComObject1` w polu **Nazwa projektu** .

4. W **Eksploratorze projektów**kliknij prawym przyciskiem `Class1`myszy, a następnie kliknij polecenie **Właściwości**. Zostanie wyświetlone okno **Właściwości** klasy.

5. Zmień wartość `Name` właściwości na `MathFunctions`.

6. W **Eksploratorze projektów**kliknij prawym przyciskiem `MathFunctions`myszy, a następnie kliknij polecenie **Wyświetl kod**. Zostanie wyświetlony **Edytor kodu** .

7. Dodaj zmienną lokalną, aby pomieścić wartość właściwości:

    ```vb
    ' Local variable to hold property value
    Private mvarProp1 As Integer
    ```

8. Dodaj właściwości `Let` `Get` i procedury właściwości właściwości:

    ```vb
    Public Property Let Prop1(ByVal vData As Integer)
       'Used when assigning a value to the property.
       mvarProp1 = vData
    End Property
    Public Property Get Prop1() As Integer
       'Used when retrieving a property's value.
       Prop1 = mvarProp1
    End Property
    ```

9. Dodaj funkcję:

    ```vb
    Function AddNumbers(
       ByVal SomeNumber As Integer,
       ByVal AnotherNumber As Integer) As Integer

       AddNumbers = SomeNumber + AnotherNumber
    End Function
    ```

10. Utwórz i zarejestruj obiekt COM, klikając pozycję **Utwórz ComObject1. dll** w menu **plik** .

    > [!NOTE]
    > Chociaż można również uwidocznić klasę utworzoną za pomocą Visual Basic jako obiekt COM, nie jest to prawdziwy obiekt COM i nie można jej użyć w tym instruktażu. Aby uzyskać szczegółowe informacje, zobacz [współdziałanie com w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).

## <a name="interop-assemblies"></a>Zestawy międzyoperacyjności

Poniższa procedura polega na utworzeniu zestawu międzyoperacyjnego, który działa jako Most między kodem niezarządzanym (takim jak obiekt COM) i zarządzanym przez program Visual Studio. Zestaw międzyoperacyjny, który Visual Basic tworzy obsługę wielu szczegółów pracy z obiektami COM, takimi jak *organizowanie międzyoperacyjności*, proces pakowania parametrów i zwracanie wartości na równoważne typy danych podczas przenoszenia ich do i z obiektów com. Odwołanie w Visual Basic wskazuje zestaw międzyoperacyjny, a nie rzeczywisty obiekt COM.

### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Aby użyć obiektu COM z Visual Basic 2005 i nowszymi wersjami

1. Otwórz nowy projekt aplikacji Visual Basic systemu Windows.

2. W menu **projekt** kliknij polecenie **Dodaj odwołanie**.

     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.

3. Na karcie **com** kliknij dwukrotnie `ComObject1` na liście **Nazwa składnika** , a następnie kliknij przycisk **OK**.

4. W menu **projekt** kliknij polecenie **Dodaj nowy element**.

     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.

5. W okienku **Szablony** kliknij pozycję **Klasa**.

     Domyślna nazwa `Class1.vb`pliku,,, pojawia się w polu **Nazwa** . Zmień to pole na MathClass. vb i kliknij przycisk **Dodaj**. Spowoduje to utworzenie klasy o `MathClass`nazwie i wyświetlenie jej kodu.

6. Dodaj następujący kod na początku `MathClass` , aby dziedziczyć z klasy com.

     [!code-vb[VbVbalrInterop#31](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#31)]

7. Przeciążać publiczną metodę klasy bazowej, dodając następujący kod do `MathClass`:

     [!code-vb[VbVbalrInterop#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#32)]

8. Poszerzenie dziedziczonej klasy przez dodanie następującego kodu do `MathClass`:

     [!code-vb[VbVbalrInterop#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#33)]

Nowa klasa dziedziczy właściwości klasy podstawowej w obiekcie COM, przeciążuje metodę i definiuje nową metodę, aby zwiększyć klasę.

### <a name="to-test-the-inherited-class"></a>Aby przetestować dziedziczonej klasy

1. Dodaj przycisk do formularza startowego, a następnie kliknij go dwukrotnie, aby wyświetlić jego kod.

2. W procedurze obsługi `Click` zdarzeń przycisku Dodaj następujący kod, aby utworzyć `MathClass` wystąpienie i wywołać przeciążone metody:

     [!code-vb[VbVbalrInterop#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrInterop/VB/Class1.vb#34)]

3. Uruchom projekt, naciskając klawisz F5.

Po kliknięciu przycisku w formularzu `AddNumbers` Metoda jest najpierw wywoływana z `Short` liczbami typu danych, a Visual Basic wybiera odpowiednią metodę z klasy bazowej. Drugie wywołanie `AddNumbers` jest kierowane do metody przeciążenia z `MathClass`. Trzecie wywołanie wywołuje `SubtractNumbers` metodę, która rozszerza klasę. Właściwość w klasie bazowej jest ustawiona i zostanie wyświetlona wartość.

## <a name="next-steps"></a>Następne kroki

Być może zauważono, że przeciążona `AddNumbers` funkcja wydaje się mieć ten sam typ danych co Metoda dziedziczona z klasy podstawowej obiektu com. Wynika to z faktu, że argumenty i parametry metody klasy bazowej są zdefiniowane jako 16-bitowe liczby całkowite w Visual Basic 6,0, ale są one widoczne jako 16-bitowe liczby całkowite typu `Short` w nowszych wersjach Visual Basic. Nowa funkcja akceptuje 32-bitowe liczby całkowite i przeciążać funkcję klasy bazowej.

Podczas pracy z obiektami COM upewnij się, że sprawdzane są rozmiary i typy danych parametrów. Na przykład podczas korzystania z obiektu COM, który akceptuje obiekt kolekcji Visual Basic 6,0 jako argument, nie można dostarczyć kolekcji z nowszej wersji Visual Basic.

Właściwości i metody dziedziczone z klas COM można przesłonić, co oznacza, że można zadeklarować lokalną właściwość lub metodę zastępującą właściwość lub metodę dziedziczoną z klasy podstawowej modelu COM. Reguły przesłaniania dziedziczonych właściwości COM są podobne do reguł zastępowania innych właściwości i metod z następującymi wyjątkami:

- W przypadku zastąpienia dowolnej właściwości lub metody odziedziczonej z klasy COM należy zastąpić wszystkie inne dziedziczone właściwości i metody.

- Właściwości używające `ByRef` parametrów nie mogą być zastępowane.

## <a name="see-also"></a>Zobacz także

- [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)
- [Inherits, instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [Short, typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
