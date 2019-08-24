---
title: 'Przewodnik: dziedziczenie z kontrolki formularzy systemu Windows formantu z Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 4a9a4b9bc15d2579837c3f4969a8d85293f10967
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015670"
---
# <a name="walkthrough-inherit-from-a-windows-forms-control-with-c"></a>Przewodnik: Dziedzicz z kontrolki Windows Forms przy użyciu języka C\#

Za pomocą C#wizualizacji można tworzyć zaawansowane niestandardowe kontrolkiprzez dziedziczenie. Za pomocą dziedziczenia można tworzyć kontrolki, które zachowują wszystkie nieodłączne funkcje standardowych formantów Windows Forms, ale również zawierają funkcje niestandardowe. W tym instruktażu utworzysz prostą dziedziczoną kontrolkę o nazwie `ValueButton`. Ten przycisk dziedziczy funkcje ze standardowego formantu Windows Forms <xref:System.Windows.Forms.Button> i uwidacznia właściwość niestandardową o nazwie. `ButtonValue`

## <a name="create-the-project"></a>Tworzenie projektu

Podczas tworzenia nowego projektu należy określić jego nazwę, aby ustawić główną przestrzeń nazw, nazwę zestawu i nazwę projektu oraz upewnić się, że domyślny składnik będzie w poprawnej przestrzeni nazw.

### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć bibliotekę kontrolek ValueButtonLib i formant ValueButton

1. W programie Visual Studio Utwórz nowy projekt **biblioteki formantów Windows Forms** i nadaj mu nazwę **ValueButtonLib**.

     Nazwa projektu, `ValueButtonLib`, również jest domyślnie przypisana do głównej przestrzeni nazw. Główna przestrzeń nazw służy do kwalifikowania nazw składników w zestawie. Na przykład jeśli dwa zestawy dostarczają składniki o nazwie `ValueButton`, można `ValueButton` określić składnik przy użyciu `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md).

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **UserControl1.cs**, a następnie wybierz polecenie **Zmień nazwę** z menu skrótów. Zmień nazwę pliku na **ValueButton.cs**. Kliknij przycisk **tak** po wyświetleniu monitu, jeśli chcesz zmienić nazwy wszystkich odwołań do elementu kodu '`UserControl1`'.

3. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs** i wybierz polecenie **Wyświetl kod**.

4. `class` Znajdź <xref:System.Windows.Forms.UserControl> <xref:System.Windows.Forms.Button>wiersz instrukcji i Zmień typ, z którego dziedziczy `public partial class ValueButton`ten formant. Dzięki temu Odziedziczone kontrolki dziedziczą wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.

5. W **Eksplorator rozwiązań**otwórz węzeł **ValueButton.cs** , aby wyświetlić plik kodu wygenerowany przez projektanta, **ValueButton.Designer.cs**. Otwórz ten plik w **edytorze kodu**.

6. Znajdź metodę i Usuń wiersz, który <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> przypisuje właściwość. `InitializeComponent` Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontrolce.

7. Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.

    > [!NOTE]
    > Projektant wizualny nie jest już dostępny. <xref:System.Windows.Forms.Button> Ponieważ kontrolka wykonuje własne malowanie, nie można modyfikować jej wyglądu w projektancie. Jego reprezentacja wizualna będzie dokładnie taka sama jak Klasa, która dziedziczy z (czyli), <xref:System.Windows.Forms.Button>chyba że zostanie zmodyfikowana w kodzie. Można nadal dodawać składniki, które nie mają elementów interfejsu użytkownika, do powierzchni projektowej.

## <a name="add-a-property-to-your-inherited-control"></a>Dodawanie właściwości do kontrolki dziedziczonej

Jednym z możliwych użycia dziedziczonych kontrolek Windows Forms jest utworzenie kontrolek, które są identyczne w wyglądzie i działaniu standardowych kontrolek Windows Forms, ale Uwidacznianie właściwości niestandardowych. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do kontrolki.

### <a name="to-add-the-value-property"></a>Aby dodać właściwość Value

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **ValueButton.cs**, a następnie kliknij pozycję **Wyświetl kod** w menu skrótów.

2. `class` Znajdź instrukcję. Natychmiast po `{`wpisz następujący kod:

    ```csharp
    // Creates the private variable that will store the value of your
    // property.
    private int varValue;
    // Declares the property.
    public int ButtonValue
    {
       // Sets the method for retrieving the value of your property.
       get
       {
          return varValue;
       }
       // Sets the method for setting the value of your property.
       set
       {
          varValue = value;
       }
    }
    ```

     Ten kod ustawia metody, za pomocą których `ButtonValue` właściwość jest przechowywana i pobierana. Instrukcja ustawia wartość zwracaną na wartość, która jest przechowywana w zmiennej `varValue`prywatnej, a `set` instrukcja ustawia wartość zmiennej prywatnej za pomocą `value` słowa kluczowego. `get`

3. Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt.

## <a name="test-the-control"></a>Testowanie kontrolki

Formanty nie są projektami autonomicznymi; muszą być hostowane w kontenerze. W celu przetestowania kontrolki musisz dostarczyć projekt testowy, aby uruchomić go w programie. Należy również udostępnić formant dla projektu testowego przez skompilowanie (skompilowanie). W tej sekcji utworzysz swój formant i przetestujesz go w formularzu systemu Windows.

### <a name="to-build-your-control"></a>Aby skompilować swój formant

Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**. Kompilacja powinna zakończyć się powodzeniem bez błędów lub ostrzeżeń kompilatora.

### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy

1. W menu **plik** wskaż polecenie **Dodaj** , a następnie kliknij pozycję **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .

2. Wybierz węzeł **systemu Windows** znajdujący się pod węzłem **wizualizacji C#**  , a następnie kliknij pozycję **Windows Forms aplikacji**.

3. W polu **Nazwa** wprowadź **test**.

4. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł **odwołania** dla projektu testowego, a następnie wybierz polecenie **Dodaj odwołanie** z menu skrótów, aby wyświetlić okno dialogowe **Dodawanie odwołania** .

5. Kliknij kartę z etykietą **projekty**. Projekt ValueButtonLib zostanie wyświetlony na liście **Nazwa projektu**. Kliknij dwukrotnie projekt, aby dodać odwołanie do projektu testowego.

6. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy pozycję **Testuj** i wybierz polecenie **Kompiluj**.

### <a name="to-add-your-control-to-the-form"></a>Aby dodać kontrolkę do formularza

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1.cs** i wybierz polecenie **View Designer** z menu skrótów.

2. W **przyborniku**wybierz pozycję **składniki ValueButtonLib**. Kliknij dwukrotnie pozycję **ValueButton**.

     **ValueButton** pojawia się w formularzu.

3. Kliknij prawym przyciskiem myszy **ValueButton** i wybierz polecenie **Właściwości** z menu skrótów.

4. W oknie **Właściwości** , przejrzyj właściwości tej kontrolki. Należy zauważyć, że są one takie same jak właściwości udostępniane przez standardowy przycisk, z tą różnicą, że istnieje dodatkowa Właściwość ButtonValue.

5. Ustaw właściwość **ButtonValue** na **5**.

6. Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie pozycję <xref:System.Windows.Forms.Label> **etykieta** , aby dodać kontrolkę do formularza.

7. Przenieś etykietę do środka formularza.

8. Kliknij `valueButton1`dwukrotnie.

     **Edytor kodu** zostanie otwarty dla `valueButton1_Click` zdarzenia.

9. Wstaw następujący wiersz kodu.

    ```csharp
    label1.Text = valueButton1.ButtonValue.ToString();
    ```

10. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **test**, a następnie wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.

11. Z menu **Debuguj** wybierz polecenie **Rozpocznij debugowanie**.

     `Form1`się.

12. Kliknij `valueButton1`pozycję.

     Liczba "5 `label1`" jest wyświetlana w, pokazując, `ButtonValue` że właściwość dziedziczonego formantu została przeniesiona do `label1` za pomocą `valueButton1_Click` metody. W ten sposób formant dziedziczy wszystkie funkcje standardowego przycisku Windows Forms, ale uwidacznia dodatkową, niestandardową właściwość. `ValueButton`

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Przewodnik: Tworzenie formantu złożonego za pomocą wizualizacjiC#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
