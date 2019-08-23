---
title: 'Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
ms.openlocfilehash: 378d7b0c67791e6c48e9859e0546594df3ccc85e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931006"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows z Visual Basic
Za pomocą Visual Basic można tworzyć zaawansowane niestandardowe kontrolki przez *dziedziczenie*. Za pomocą dziedziczenia można tworzyć kontrolki, które zachowują wszystkie nieodłączne funkcje standardowych formantów Windows Forms, ale również zawierają funkcje niestandardowe. W tym instruktażu utworzysz prostą dziedziczoną kontrolkę o nazwie `ValueButton`. Ten przycisk dziedziczy funkcje ze standardowego formantu Windows Forms <xref:System.Windows.Forms.Button> i uwidacznia właściwość niestandardową o nazwie. `ButtonValue`

## <a name="creating-the-project"></a>Tworzenie projektu
 Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnej przestrzeni nazw.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć bibliotekę kontrolek ValueButtonLib i formant ValueButton

1. W menu **plik** wskaż polecenie **Nowy** , a następnie kliknij pozycję **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

2. Wybierz szablon projektu **Biblioteka formantów Windows Forms** z listy projektów Visual Basic i wpisz `ValueButtonLib` w polu **Nazwa** .

     Nazwa projektu, `ValueButtonLib`, również jest domyślnie przypisana do głównej przestrzeni nazw. Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie. Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ValueButton`, można `ValueButton` określić składnik przy użyciu `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw w Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md).

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1. vb**, a następnie wybierz polecenie **Zmień nazwę** z menu skrótów. Zmień nazwę pliku na `ValueButton.vb`. Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwę wszystkich odwołań do elementu kodu "UserControl1".

4. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .

5. Otwórz węzeł **ValueButton. vb** , aby wyświetlić plik kodu wygenerowany przez projektanta, **ValueButton. Designer. vb**. Otwórz ten plik w **edytorze kodu**.

6. `Class` Znajdź <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>instrukcję iZmieńtyp,zktóregota`Partial Public Class ValueButton`kontrolka dziedziczy. Dzięki temu Odziedziczone kontrolki dziedziczą wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.

7. Znajdź metodę i Usuń wiersz, który <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> przypisuje właściwość. `InitializeComponent` Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontrolce.

8. Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.

     Należy zauważyć, że projektant wizualny nie jest już dostępny. <xref:System.Windows.Forms.Button> Ponieważ kontrolka wykonuje własne malowanie, nie można modyfikować jej wyglądu w projektancie. Jego reprezentacja wizualna będzie dokładnie taka sama jak Klasa, która dziedziczy z (czyli), <xref:System.Windows.Forms.Button>chyba że zostanie zmodyfikowana w kodzie.

> [!NOTE]
> Można nadal dodawać składniki, które nie mają elementów interfejsu użytkownika, do powierzchni projektowej.

## <a name="adding-a-property-to-your-inherited-control"></a>Dodawanie właściwości do kontrolki dziedziczonej
 Jednym z możliwych użycia dziedziczonych kontrolek Windows Forms jest tworzenie formantów, które są identyczne w wyglądzie i zachowaniu (wygląd i działanie) w standardowych kontrolkach Windows Forms, ale uwidaczniają właściwości niestandardowe. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do kontrolki.

### <a name="to-add-the-value-property"></a>Aby dodać właściwość Value

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy **ValueButton. vb**, a następnie kliknij polecenie **Wyświetl kod** w menu skrótów.

2. `Public Class ValueButton` Znajdź instrukcję. Bezpośrednio poniżej tej instrukcji wpisz następujący kod:

    ```vb
    ' Creates the private variable that will store the value of your
    ' property.
    Private varValue as integer
    ' Declares the property.
    Property ButtonValue() as Integer
    ' Sets the method for retrieving the value of your property.
       Get
          Return varValue
       End Get
    ' Sets the method for setting the value of your property.
       Set(ByVal Value as Integer)
          varValue = Value
       End Set
    End Property
    ```

     Ten kod ustawia metody, za pomocą których `ButtonValue` właściwość jest przechowywana i pobierana. Instrukcja ustawia wartość zwracaną na wartość, która jest przechowywana w zmiennej `varValue`prywatnej, a `Set` instrukcja ustawia wartość zmiennej prywatnej za pomocą `Value` słowa kluczowego. `Get`

3. Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.

## <a name="testing-your-control"></a>Testowanie kontrolki
 Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze. W celu przetestowania kontrolki musisz dostarczyć projekt testowy, aby uruchomić go w programie. Należy również udostępnić formant dla projektu testowego przez skompilowanie (skompilowanie). W tej sekcji utworzysz swój formant i przetestujesz go w formularzu systemu Windows.

### <a name="to-build-your-control"></a>Aby skompilować swój formant

1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.

     Kompilacja powinna zakończyć się powodzeniem bez błędów lub ostrzeżeń kompilatora.

### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy

1. W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .

2. Wybierz węzeł projekty Visual Basic, a następnie kliknij pozycję **Windows Forms aplikacji**.

3. W polu **Nazwa** wpisz `Test`.

4. W **Eksplorator rozwiązań**kliknij przycisk **Pokaż wszystkie pliki** .

5. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego, a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów, aby wyświetlić okno dialogowe **Dodawanie odwołania** .

6. Kliknij kartę **projekty** .

7. Kliknij kartę z etykietą **projekty**. Projekt zostanie wyświetlony na liście **Nazwa projektu.** `ValueButtonLib` Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.

8. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Testuj** i wybierz polecenie **Kompiluj**.

### <a name="to-add-your-control-to-the-form"></a>Aby dodać kontrolkę do formularza

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1. vb** i wybierz polecenie **Projektant widoków** z menu skrótów.

2. W **przyborniku**kliknij pozycję **składniki ValueButtonLib**. Kliknij dwukrotnie pozycję **ValueButton**.

     **ValueButton** pojawia się w formularzu.

3. Kliknij prawym przyciskiem myszy **ValueButton** i wybierz polecenie **Właściwości** z menu skrótów.

4. W oknie **Właściwości** , przejrzyj właściwości tej kontrolki. Należy zauważyć, że są one takie same jak właściwości udostępniane przez standardowy przycisk, z tą różnicą, że istnieje `ButtonValue`dodatkowa właściwość.

5. Ustaw `ButtonValue` właściwość `5`.

6. Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie pozycję <xref:System.Windows.Forms.Label> **etykieta** , aby dodać kontrolkę do formularza.

7. Przenieś etykietę do środka formularza.

8. Kliknij `ValueButton1`dwukrotnie.

     **Edytor kodu** zostanie otwarty dla `ValueButton1_Click` zdarzenia.

9. Wpisz następujący wiersz kodu.

    ```vb
    Label1.Text = CStr(ValueButton1.ButtonValue)
    ```

10. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.

11. Z menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.

     `Form1`się.

12. Kliknij `Valuebutton1`pozycję.

     Liczba "5 `Label1`" jest wyświetlana w, pokazując, `ButtonValue` że właściwość dziedziczonego formantu została przeniesiona do `Label1` za pomocą `ValueButton1_Click` metody. W ten sposób formant dziedziczy wszystkie funkcje standardowego przycisku Windows Forms, ale uwidacznia dodatkową, niestandardową właściwość. `ValueButton`

## <a name="see-also"></a>Zobacz także

- [Przewodnik: Tworzenie złożonego formantu z Visual Basic](walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Podstawowe informacje o dziedziczeniu (Visual Basic)](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
