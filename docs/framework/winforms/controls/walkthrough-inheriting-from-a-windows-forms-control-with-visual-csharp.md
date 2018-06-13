---
title: 'Wskazówki: dziedziczenie z formularzy systemu Windows formantu z Visual C#'
ms.date: 03/30/2017
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: 09476da0-8d4c-4a4c-b969-649519dfb438
ms.openlocfilehash: 1e9231065369640fa49e04a491b92ebfb1e91912
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33541512"
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-c"></a>Wskazówki: dziedziczenie z formularzy systemu Windows formantu z Visual C# #
Z [!INCLUDE[csprcslong](../../../../includes/csprcslong-md.md)], możesz utworzyć zaawansowane formantów niestandardowych za pomocą *dziedziczenia*. Poprzez dziedziczenie jest możliwość tworzenia formantów, które zachowują wszystkie funkcje związane z standardowe formanty formularzy systemu Windows, ale także dołączyć do nich funkcji niestandardowych. W tym przewodniku spowoduje utworzenie prostego formantu dziedziczone o nazwie `ValueButton`. Ten przycisk będzie dziedziczyć funkcje z formularzy systemu Windows <xref:System.Windows.Forms.Button> kontroli i uwidoczni właściwość niestandardowa o nazwie `ButtonValue`.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć biblioteki formantu ValueButtonLib i kontroli ValueButton  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Wybierz **Biblioteka formantów formularzy systemu Windows** szablon projektu na liście Projekty Visual C#, a typ `ValueButtonLib` w **nazwa** pole.  
  
     Nazwa projektu `ValueButtonLib`, jest również przypisany do głównej przestrzeni nazw domyślnie. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, można określić użytkownika `ValueButton` przy użyciu składnika `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzeni nazw](../../../csharp/programming-guide/namespaces/index.md).  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.cs**, a następnie wybierz **zmienić** z menu skrótów. Zmień nazwę pliku, aby `ValueButton.cs`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu '`UserControl1`".  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs** i wybierz **kod widoku**.  
  
5.  Zlokalizuj `class` wiersz instrukcji `public partial class ValueButton`i zmienić typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>. Dzięki temu dziedziczone formantu dziedziczy wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.  
  
6.  W **Eksploratora rozwiązań**, otwórz **ValueButton.cs** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.cs**. Otwórz ten plik w **edytora kodu**.  
  
7.  Zlokalizuj `InitializeComponent` — metoda i Usuń wiersz, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości. Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> formantu.  
  
8.  Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.  
  
    > [!NOTE]
    >  Projektant wizualny nie jest już dostępny. Ponieważ <xref:System.Windows.Forms.Button> formant wykonuje własny obraz, nie można zmodyfikować jego wygląd w projektancie. Jego wizualnej reprezentacji będą dokładnie taka sama jak klasa dziedziczy z (czyli <xref:System.Windows.Forms.Button>), chyba że zmodyfikowany w kodzie. Nadal możesz dodać składniki, które mają żadnych elementów interfejsu użytkownika, na powierzchnię projektu.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Dodawanie właściwości do dziedziczonej formantu  
 Jeden wykorzystanie dziedziczone formanty formularzy systemu Windows jest tworzenie formantów, które są takie same jak w wygląd i działanie standardowe formanty formularzy systemu Windows, ale udostępniają właściwości niestandardowych. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.  
  
#### <a name="to-add-the-value-property"></a>Aby dodać właściwości Value  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.cs**, a następnie kliknij przycisk **kod widoku** z menu skrótów.  
  
2.  Zlokalizuj `class` instrukcji. Natychmiast po `{`, wpisz następujący kod:  
  
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
  
     Ten kod ustawia metody za pomocą której `ButtonValue` przechowywania i pobierania właściwości. `get` Instrukcja ustawia wartości zwracanej wartości, który jest przechowywany w prywatnej zmiennej `varValue`i `set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `value` — słowo kluczowe.  
  
3.  Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.  
  
## <a name="testing-your-control"></a>Testowanie formantu  
 Formanty nie są autonomicznych projektów; muszą one być obsługiwane w kontenerze. W celu przetestowania formantu, należy podać projekt testowy na jej uruchamianie. Należy również upewnić formantu dostępne dla projektu testowego według budynków (Kompilacja) go. W tej sekcji zostanie kompilacji formantu i przetestować go w formularzu systemu Windows.  
  
#### <a name="to-build-your-control"></a>Tworzenie formantu  
  
1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Kompilacja zostanie pomyślnie zakończona bez błędów lub ostrzeżeń.  
  
#### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy  
  
1.  Na **pliku** menu wskaż **Dodaj** , a następnie kliknij przycisk **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.  
  
2.  Wybierz **Windows** węzła, podrzędne **Visual C#** węzeł, a następnie kliknij przycisk **aplikacji Windows Forms**.  
  
3.  W **nazwa** wpisz `Test`.  
  
4.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła dla projektu testowego, następnie wybierz **Dodaj odwołanie** z menu skrótów do wyświetlenia  **Dodaj odwołanie** okno dialogowe.  
  
5.  Kliknij kartę **projekty**. Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie plik projektu można dodać odwołania do projektu testowego.  
  
6.  W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Aby dodać formantu do formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **pliku Form1.cs** i wybierz polecenie **Widok projektanta** z menu skrótów.  
  
2.  W **przybornika**, kliknij przycisk **składniki ValueButtonLib**. Kliknij dwukrotnie **ValueButton**.  
  
     A **ValueButton** w formularzu.  
  
3.  Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.  
  
4.  W **właściwości** okna, sprawdź właściwości tego formantu. Należy pamiętać, są takie same jak właściwości udostępniane przez przycisk standardowy, z tą różnicą, że jest właściwością dodatkowe `ButtonValue`.  
  
5.  Ustaw `ButtonValue` właściwości `5`.  
  
6.  W **wszystkich formularzy systemu Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** można dodać <xref:System.Windows.Forms.Label> sterowania do formularza.  
  
7.  Przemieszczenie etykietę do Centrum formularza.  
  
8.  Kliknij dwukrotnie `valueButton1`.  
  
     **Edytora kodu** otwiera `valueButton1_Click` zdarzeń.  
  
9. Wstaw następujący wiersz kodu.  
  
    ```csharp  
    label1.Text = valueButton1.ButtonValue.ToString();  
    ```  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.  
  
11. Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.  
  
     `Form1` zostanie wyświetlone.  
  
12. Kliknij przycisk `valueButton1`.  
  
     Liczb, "5" jest wyświetlany w `label1`, ilustrujące który `ButtonValue` właściwości dziedziczone formantu został przekazany do `label1` za pośrednictwem `valueButton1_Click` metody. W związku z tym Twoje `ValueButton` kontrola dziedziczy wszystkie funkcje standardowej przycisku formularzy systemu Windows, ale udostępnia dodatkowe, niestandardowe właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Programowanie przy użyciu składników](http://msdn.microsoft.com/library/d4d4fcb4-e0b8-46b3-b679-7ee0026eb9e3)  
 [Wskazówki dotyczące tworzenia składników](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual C#](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-csharp.md)
