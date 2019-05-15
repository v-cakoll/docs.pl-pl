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
ms.openlocfilehash: dc9abbf520d3af79a2c64884adcdfa2f1066ce1b
ms.sourcegitcommit: 682c64df0322c7bda016f8bfea8954e9b31f1990
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2019
ms.locfileid: "65558000"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>Przewodnik: Dziedziczenie z kontrolki formularzy Windows Forms przy użyciu języka Visual C\#
Z wizualizacją C#, można tworzyć zaawansowane Kontrolki niestandardowe za pomocą *dziedziczenia*. Poprzez dziedziczenie jest możliwe w celu tworzenia formantów, które zachować wszystkie związane funkcje standardowych kontrolek Windows Forms, ale również dołączać niestandardowe funkcje. W tym instruktażu utworzysz prostą odziedziczoną kontrolkę o nazwie `ValueButton`. Ten przycisk będzie dziedziczyć funkcji z formularzy Windows <xref:System.Windows.Forms.Button> kontrolować i udostępni właściwość niestandardową o nazwie `ButtonValue`.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu, należy określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślną będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć ValueButtonLib Biblioteka kontrolek i kontrola ValueButton  
  
1. Na **pliku** menu wskaż **New** a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2. Wybierz **Biblioteka kontrolek formularzy Windows** szablonu projektu z listy projektów programu Visual C# i typu `ValueButtonLib` w **nazwa** pole.  
  
     Nazwa projektu `ValueButtonLib`, również jest domyślnie przypisane do głównej przestrzeni nazw. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, możesz określić swoje `ValueButton` za pomocą składnika `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzenie nazw](../../../csharp/programming-guide/namespaces/index.md).  
  
3. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.cs**, następnie wybierz **Zmień nazwę** z menu skrótów. Zmień nazwę pliku, aby `ValueButton.cs`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu '`UserControl1`".  
  
4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs** i wybierz **Wyświetl kod**.  
  
5. Znajdź `class` wiersz instrukcji `public partial class ValueButton`, a następnie zmień typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>. Dzięki temu Twoje odziedziczoną kontrolkę dziedziczyć wszystkie funkcje programu <xref:System.Windows.Forms.Button> kontroli.  
  
6. W **Eksploratora rozwiązań**, otwórz **ValueButton.cs** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.cs**. Otwórz ten plik w **Edytor kodu**.  
  
7. Znajdź `InitializeComponent` metody i usunąć wiersza, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości. Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> kontroli.  
  
8. Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.  
  
    > [!NOTE]
    >  Projektant wizualny nie jest już dostępna. Ponieważ <xref:System.Windows.Forms.Button> formantu nie swój własny rysowania, nie można zmodyfikować jego wygląd w projektancie. Jego wizualnej reprezentacji będzie dokładnie taka sama jak klasa dziedziczy (czyli <xref:System.Windows.Forms.Button>) o ile nie zmodyfikowano w kodzie. Składniki, które mają bez elementów interfejsu użytkownika, można nadal dodawać do powierzchni projektowej.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Dodawanie właściwości do kontrolki dziedziczone  
 Jedno możliwe użycie dziedziczone kontrolek Windows Forms jest tworzenie elementów sterujących, które są identyczne w wygląd i działanie standardowych kontrolek Windows Forms, ale udostępnianie właściwości niestandardowych. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.  
  
#### <a name="to-add-the-value-property"></a>Aby dodać właściwość wartość  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs**, a następnie kliknij przycisk **Wyświetl kod** z menu skrótów.  
  
2. Znajdź `class` instrukcji. Natychmiast po `{`, wpisz następujący kod:  
  
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
  
     Ten kod ustawia metody za pomocą którego `ButtonValue` właściwości przechowywania i pobierania. `get` Instrukcja ustawia wartości zwracanej wartości, która jest przechowywana w zmiennej prywatnej `varValue`i `set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `value` — słowo kluczowe.  
  
3. Z **pliku** menu, wybierz **Zapisz wszystko** być zapisany projekt.  
  
## <a name="testing-your-control"></a>Testowanie formantu  
 Formanty nie są autonomiczne projektów; muszą one być obsługiwane w kontenerze. Aby przetestować Twoją kontrolą, musisz podać projekt testowy dla niego do uruchamiania w. Należy również upewnić kontroli nad dostępne dla projektu testowego, tworząc (Kompilacja) go. W tej sekcji utworzysz formant i przetestować ją w formularzu Windows.  
  
#### <a name="to-build-your-control"></a>Tworzenie formantu  
  
1. Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Kompilacja zostanie pomyślnie zakończona bez błędów i ostrzeżeń.  
  
#### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy  
  
1. Na **pliku** menu wskaż **Dodaj** a następnie kliknij przycisk **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.  
  
2. Wybierz **Windows** węzła, podrzędne **Visual C#** węzeł, a następnie kliknij przycisk **aplikacja interfejsu Windows Forms**.  
  
3. W **nazwa** wpisz `Test`.  
  
4. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzeł dla projektu testowego, następnie wybierz pozycję **Dodaj odwołanie** z menu skrótów, aby wyświetlić  **Dodaj odwołanie** okno dialogowe.  
  
5. Kliknij kartę **projektów**. Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie projektu można dodać odwołania do projektu testowego.  
  
6. W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Aby dodać formant do formularza  
  
1. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.cs** i wybierz polecenie **Projektant widoków** z menu skrótów.  
  
2. W **przybornika**, kliknij przycisk **składniki ValueButtonLib**. Kliknij dwukrotnie **ValueButton**.  
  
     A **ValueButton** pojawia się w formularzu.  
  
3. Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.  
  
4. W **właściwości** okna, sprawdź właściwości tej kontrolki. Należy pamiętać, są identyczne z właściwości ujawnione przez przycisk standardowy, z tą różnicą, że istnieje dodatkowa właściwość `ButtonValue`.  
  
5. Ustaw `ButtonValue` właściwość `5`.  
  
6. W **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** dodać <xref:System.Windows.Forms.Label> formantu do formularza.  
  
7. Przenieś etykietę do środka formularza.  
  
8. Kliknij dwukrotnie `valueButton1`.  
  
     **Edytor kodu** otwiera `valueButton1_Click` zdarzeń.  
  
9. Wstaw następujący wiersz kodu.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.  
  
11. Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.  
  
     `Form1` zostanie wyświetlone.  
  
12. Kliknij przycisk `valueButton1`.  
  
     Cyfry, '5' jest wyświetlana w `label1`, pokazując, `ButtonValue` właściwości dziedziczonych formant został przekazany do `label1` za pośrednictwem `valueButton1_Click` metody. Ten sposób Twoja `ValueButton` kontrola dziedziczy wszystkie funkcje standardowe przycisku Windows Forms, ale udostępnia dodatkowe, niestandardowe właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Wyświetlanie kontroli w wybierz elementy przybornika — okno dialogowe](how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)
- [Przewodnik: Tworzenie formantu złożonego za pomocą Visual C#](walkthrough-authoring-a-composite-control-with-visual-csharp.md)
