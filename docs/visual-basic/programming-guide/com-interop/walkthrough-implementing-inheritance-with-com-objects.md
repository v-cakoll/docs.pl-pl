---
title: "Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- inheritance [Visual Basic], COM reusability
- base classes [Visual Basic], COM reusability
- inheritance [Visual Basic], walkthroughs
- derived classes [Visual Basic], COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 8d6906c58431a0e844e8f430ade10ae819e77ff2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Wskazówki: wdrażanie dziedziczenia z obiektami COM (Visual Basic)
Mogą pochodzić klas języka Visual Basic z `Public` klasy obiektów COM, nawet te utworzone we wcześniejszych wersjach [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]. Zastąpiona lub przeciążony podobnie jak właściwości właściwości i metody dziedziczone z obiektami COM klasy i metody innych klasy podstawowej można zastąpić lub przeciążony. Dziedziczenia z obiektami COM jest przydatne w przypadku istniejącej biblioteki klas, którego chcesz ponownie skompilować.  
  
 Poniższa procedura pokazuje, jak Visual Basic 6.0 do utworzenia obiektu COM, który zawiera klasę, a następnie użyć jej jako klasę podstawową.  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Aby utworzyć obiekt COM, który jest używany w tym przewodniku  
  
1.  Otwórz nowy projekt ActiveX biblioteki DLL w Visual Basic 6.0. Projekt o nazwie `Project1` jest tworzony. Ma klasę o nazwie `Class1`.  
  
2.  W **Eksplorator projektów**, kliknij prawym przyciskiem myszy **Project1**, a następnie kliknij przycisk **Project1 właściwości**. **Właściwości projektu** zostanie wyświetlone okno dialogowe.  
  
3.  Na **ogólne** karcie **właściwości projektu** okno dialogowe Zmień nazwę projektu, wpisując `ComObject1` w **Nazwa projektu** pola.  
  
4.  W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `Class1`, a następnie kliknij przycisk **właściwości**. **Właściwości** zostanie wyświetlone okno klasy.  
  
5.  Zmień `Name` właściwości `MathFunctions`.  
  
6.  W **Eksplorator projektów**, kliknij prawym przyciskiem myszy `MathFunctions`, a następnie kliknij przycisk **kod widoku**. **Edytora kodu** jest wyświetlany.  
  
7.  Dodawanie zmiennej lokalnej do przechowywania wartości właściwości:  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Dodaj właściwość `Let` i właściwość `Get` procedury właściwości:  
  
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
  
9. Dodaj funkcję:  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Tworzenie i zarejestrować obiektu COM, klikając **upewnij ComObject1.dll** na **pliku** menu.  
  
    > [!NOTE]
    >  Mimo że można również ujawniać utworzone za pomocą klasy [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] jako obiekt COM nie jest obiektem COM. wartość true i nie można użyć w tym przewodniku. Aby uzyskać więcej informacji, zobacz [współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Zestawy międzyoperacyjne  
 W poniższej procedury spowoduje utworzenie zestawu międzyoperacyjnego, który działa jako mostka między kodu niezarządzanego (np. obiekt COM) i kod zarządzany [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)] używa. Zestaw międzyoperacyjny który [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] tworzy uchwytów wielu szczegółów pracy z COM obiekty, takie jak *przekazywanie międzyoperacyjne*, proces tworzenia pakietów parametrów i zwracanych wartości na dane równoważne typy jako przechodzą do i z modelu COM obiektów. Odwołania w [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] punktów aplikacji do zestawu międzyoperacyjnego, a nie rzeczywiste obiektu COM.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Aby użyć obiektów COM z Visual Basic 2005 lub nowszym  
  
1.  Otwórz nowe [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] projekt aplikacji systemu Windows.  
  
2.  Na **projektu** menu, kliknij przycisk **Dodaj odwołanie**.  
  
     **Dodaj odwołanie** zostanie wyświetlone okno dialogowe.  
  
3.  Na **COM** karcie, kliknij dwukrotnie `ComObject1` w **nazwa składnika** listy i kliknij przycisk **OK**.  
  
4.  Na **projektu** menu, kliknij przycisk **Dodaj nowy element**.  
  
     **Dodaj nowy element** zostanie wyświetlone okno dialogowe.  
  
5.  W **szablony** okienku, kliknij przycisk **klasy**.  
  
     Domyślna nazwa pliku `Class1.vb`, zostanie wyświetlony w **nazwa** pola. Zmień to pole na MathClass.vb i kliknij przycisk **Dodaj**. Spowoduje to utworzenie klasy o nazwie `MathClass`i wyświetla jego kod.  
  
6.  Dodaj następujący kod do góry `MathClass` dziedziczona z klasy COM.  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Przeciążenia publicznej metody klasy podstawowej, dodając następujący kod do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Rozszerzenie klasy dziedziczonej, dodając następujący kod do `MathClass`:  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 Nowa klasa dziedziczy właściwości klasy podstawowej w obiekcie COM, overloads metody i definiuje nową metodę rozszerzenie klasy.  
  
#### <a name="to-test-the-inherited-class"></a>Aby przetestować dziedziczonej klasie  
  
1.  Dodawanie przycisku do formularza uruchamiania, a następnie kliknij dwukrotnie, aby wyświetlić jego kod.  
  
2.  Przycisk `Click` procedury obsługi zdarzeń, Dodaj następujący kod, aby utworzyć wystąpienie `MathClass` i wywoływać przeciążenia metody:  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  Uruchom projekt, naciskając klawisz F5.  
  
 Po kliknięciu przycisku w formularzu `AddNumbers` najpierw wywoływana jest metoda o `Short` typ danych liczb, i [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] wybiera odpowiednią metodę z klasy podstawowej. Drugie wywołanie `AddNumbers` zostaje skierowany do przeciążenia metody z `MathClass`. Trzeci wywołania wywołania `SubtractNumbers` metodę, która rozszerza klasę. Ustawiono właściwości w klasie podstawowej, a wartość jest wyświetlana.  
  
## <a name="next-steps"></a>Następne kroki  
 Można zauważyć, że przeciążenia `AddNumbers` funkcja wydaje się mają ten sam typ jako metody dziedziczona z klasy podstawowej obiektu COM danych. Wynika to z faktu, argumentów i parametrów metody klasy podstawowej są zdefiniowane jako 16-bitowych liczb całkowitych w Visual Basic 6.0, ale są one widoczne jako 16-bitowych liczb całkowitych typu `Short` w nowszych wersjach programu Visual Basic. Nowa funkcja akceptuje 32-bitowych liczb całkowitych i overloads funkcji klasy podstawowej.  
  
 Podczas pracy z obiektami COM, upewnij się, że należy sprawdzić rozmiar i danych typów parametrów. Na przykład jeśli używasz obiektu COM, który akceptuje obiekt kolekcji Visual Basic 6.0 jako argument nie może dostarczyć kolekcji z nowszej wersji programu Visual Basic.  
  
 Właściwości i metody odziedziczona z klasy COM może zostać zastąpiona, co oznacza, że można zadeklarować lokalnego właściwości lub metody, które zastępuje właściwość lub dziedziczone z podstawową klasę com. Zasady zastępowania odziedziczone właściwości modelu COM są podobne do reguły zastępowania inne właściwości i metody z następującymi wyjątkami:  
  
-   Należy zastąpić wszystkie właściwości lub metody odziedziczona z klasy COM, należy zastąpić wszystkie odziedziczone właściwości i metody.  
  
-   Właściwości, które używają `ByRef` parametrów nie może zostać zastąpiona.  
  
## <a name="see-also"></a>Zobacz też  
 [Współdziałanie COM w aplikacjach .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)  
 [Inherits — instrukcja](../../../visual-basic/language-reference/statements/inherits-statement.md)  
 [Short — typ danych](../../../visual-basic/language-reference/data-types/short-data-type.md)
