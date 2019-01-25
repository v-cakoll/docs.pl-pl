---
title: 'Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic'
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
ms.openlocfilehash: 157c323a2536f1034b7a8ceace630a9e15168552
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54728138"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms za pomocą Visual Basic
Za pomocą Visual Basic można tworzyć zaawansowane Kontrolki niestandardowe za pomocą *dziedziczenia*. Poprzez dziedziczenie jest możliwe w celu tworzenia formantów, które zachować wszystkie związane funkcje standardowych kontrolek Windows Forms, ale również dołączać niestandardowe funkcje. W tym instruktażu utworzysz prostą odziedziczoną kontrolkę o nazwie `ValueButton`. Ten przycisk będzie dziedziczyć funkcji z formularzy Windows <xref:System.Windows.Forms.Button> kontrolować i udostępni właściwość niestandardową o nazwie `ButtonValue`.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu, należy określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć ValueButtonLib Biblioteka kontrolek i kontrola ValueButton  
  
1.  Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Wybierz **Biblioteka kontrolek formularzy Windows** szablonu projektu z listy projektów języka Visual Basic, a typ `ValueButtonLib` w **nazwa** pole.  
  
     Nazwa projektu `ValueButtonLib`, również jest domyślnie przypisane do głównej przestrzeni nazw. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, możesz określić swoje `ValueButton` za pomocą składnika `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w języku Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.vb**, następnie wybierz **Zmień nazwę** z menu skrótów. Zmień nazwę pliku, aby `ValueButton.vb`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
5.  Otwórz **ValueButton.vb** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.vb**. Otwórz ten plik w **Edytor kodu**.  
  
6.  Znajdź `Class` instrukcji `Partial Public Class ValueButton`, a następnie zmień typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>. Dzięki temu Twoje odziedziczoną kontrolkę dziedziczyć wszystkie funkcje programu <xref:System.Windows.Forms.Button> kontroli.  
  
7.  Znajdź `InitializeComponent` metody i usunąć wiersza, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości. Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontroli.  
  
8.  Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.  
  
     Należy pamiętać, że projektant wizualny nie jest już dostępna. Ponieważ <xref:System.Windows.Forms.Button> formantu nie swój własny rysowania, nie można zmodyfikować jego wygląd w projektancie. Jego wizualnej reprezentacji będzie dokładnie taka sama jak klasa dziedziczy (czyli <xref:System.Windows.Forms.Button>) o ile nie zmodyfikowano w kodzie.  
  
> [!NOTE]
>  Składniki, które mają bez elementów interfejsu użytkownika, można nadal dodawać do powierzchni projektowej.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Dodawanie właściwości do kontrolki dziedziczone  
 Jedno możliwe użycie dziedziczone kontrolek Windows Forms jest tworzenie elementów sterujących, które są takie same jak w wygląd i zachowanie (wyglądu i działania) standardowych kontrolek Windows Forms, ale udostępnianie właściwości niestandardowych. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.  
  
#### <a name="to-add-the-value-property"></a>Aby dodać właściwość wartość  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.vb**, a następnie kliknij przycisk **Wyświetl kod** z menu skrótów.  
  
2.  Znajdź `Public Class ValueButton` instrukcji. Natychmiast poniżej tej instrukcji, wpisz następujący kod:  
  
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
  
     Ten kod ustawia metody za pomocą którego `ButtonValue` właściwości przechowywania i pobierania. `Get` Instrukcja ustawia wartości zwracanej wartości, która jest przechowywana w zmiennej prywatnej `varValue`i `Set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `Value` — słowo kluczowe.  
  
3.  Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.  
  
## <a name="testing-your-control"></a>Testowanie formantu  
 Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze. Aby przetestować Twoją kontrolą, musisz podać projekt testowy dla niego do uruchamiania w. Należy również upewnić kontroli nad dostępne dla projektu testowego, tworząc (Kompilacja) go. W tej sekcji utworzysz formant i przetestować ją w formularzu Windows.  
  
#### <a name="to-build-your-control"></a>Tworzenie formantu  
  
1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Kompilacja zostanie pomyślnie zakończona bez błędów i ostrzeżeń.  
  
#### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy  
  
1.  Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.  
  
2.  Wybierz węzeł projektów języka Visual Basic, a następnie kliknij przycisk **aplikacja interfejsu Windows Forms**.  
  
3.  W **nazwa** wpisz `Test`.  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego, następnie wybierz pozycję **Dodaj odwołanie** z menu skrótów, aby wyświetlić  **Dodaj odwołanie** okno dialogowe.  
  
6.  Kliknij przycisk **projektów** kartę.  
  
7.  Kliknij kartę **projektów**. Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.  
  
8.  W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Aby dodać formant do formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb** i wybierz polecenie **Projektant widoków** z menu skrótów.  
  
2.  W **przybornika**, kliknij przycisk **składniki ValueButtonLib**. Kliknij dwukrotnie **ValueButton**.  
  
     A **ValueButton** pojawia się w formularzu.  
  
3.  Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.  
  
4.  W **właściwości** okna, sprawdź właściwości tej kontrolki. Należy pamiętać, są identyczne z właściwości ujawnione przez przycisk standardowy, z tą różnicą, że istnieje dodatkowa właściwość `ButtonValue`.  
  
5.  Ustaw `ButtonValue` właściwość `5`.  
  
6.  Na **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** dodać <xref:System.Windows.Forms.Label> formantu do formularza.  
  
7.  Przenieś etykietę do środka formularza.  
  
8.  Kliknij dwukrotnie `ValueButton1`.  
  
     **Edytor kodu** otwiera `ValueButton1_Click` zdarzeń.  
  
9. Wpisz następujący wiersz kodu.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.  
  
11. Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.  
  
     `Form1` zostanie wyświetlone.  
  
12. Kliknij przycisk `Valuebutton1`.  
  
     Cyfry, '5' jest wyświetlana w `Label1`, pokazując, `ButtonValue` właściwości dziedziczonych formant został przekazany do `Label1` za pośrednictwem `ValueButton1_Click` metody. Ten sposób Twoja `ValueButton` kontrola dziedziczy wszystkie funkcje standardowe przycisku Windows Forms, ale udostępnia dodatkowe, niestandardowe właściwości.  
  
## <a name="see-also"></a>Zobacz także
- [Przewodnik: Tworzenie formantu złożonego za pomocą Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)
- [Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)
- [Podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [Tworzenie składników — wskazówki](https://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
