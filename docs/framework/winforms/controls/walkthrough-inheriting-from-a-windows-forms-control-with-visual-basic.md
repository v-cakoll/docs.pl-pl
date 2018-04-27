---
title: 'Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- vb
helpviewer_keywords:
- inheritance [Windows Forms], custom controls
- inheritance [Windows Forms], control
- Windows Forms controls, inheritance
- inheritance [Windows Forms], walkthroughs
- custom controls [Windows Forms], inheritance
ms.assetid: fb58d7c8-b702-4478-ad31-b00cae118882
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 342ab60d4c3481d2154293fab9fb1254f937a934
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="walkthrough-inheriting-from-a-windows-forms-control-with-visual-basic"></a>Wskazówki: dziedziczenie z formantu formularzy systemu Windows z Visual Basic
Visual Basic umożliwia tworzenie zaawansowanych formantów niestandardowych za pomocą *dziedziczenia*. Poprzez dziedziczenie jest możliwość tworzenia formantów, które zachowują wszystkie funkcje związane z standardowe formanty formularzy systemu Windows, ale także dołączyć do nich funkcji niestandardowych. W tym przewodniku spowoduje utworzenie prostego formantu dziedziczone o nazwie `ValueButton`. Ten przycisk będzie dziedziczyć funkcje z formularzy systemu Windows <xref:System.Windows.Forms.Button> kontroli i uwidoczni właściwość niestandardowa o nazwie `ButtonValue`.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Podczas tworzenia nowego projektu można określić jego nazwę, aby ustawić głównej przestrzeni nazw, nazwa zestawu i nazwa projektu i upewnij się, że składnik domyślna będzie poprawną przestrzeń nazw.  
  
#### <a name="to-create-the-valuebuttonlib-control-library-and-the-valuebutton-control"></a>Aby utworzyć biblioteki formantu ValueButtonLib i kontroli ValueButton  
  
1.  Na **pliku** menu wskaż **nowy** , a następnie kliknij przycisk **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Wybierz **Biblioteka formantów formularzy systemu Windows** szablonu projektu z listy projektów Visual Basic i typ `ValueButtonLib` w **nazwa** pole.  
  
     Nazwa projektu `ValueButtonLib`, jest również przypisany do głównej przestrzeni nazw domyślnie. Główna przestrzeń nazw są używane do kwalifikowania nazwy elementów w zestawie. Na przykład, jeśli dwa zestawy zawiera składniki o nazwie `ValueButton`, można określić użytkownika `ValueButton` przy użyciu składnika `ValueButtonLib.ValueButton`. Aby uzyskać więcej informacji, zobacz [przestrzeni nazw w Visual Basic](~/docs/visual-basic/programming-guide/program-structure/namespaces.md).  
  
3.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **UserControl1.vb**, a następnie wybierz **zmienić** z menu skrótów. Zmień nazwę pliku, aby `ValueButton.vb`. Kliknij przycisk **tak** przycisku, gdy zostanie wyświetlony monit, jeśli chcesz zmienić wszystkie odwołania do elementu kodu "UserControl1".  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
5.  Otwórz **ValueButton.vb** węzeł, aby wyświetlić plik kod wygenerowany przez projektanta **ValueButton.Designer.vb**. Otwórz ten plik w **edytora kodu**.  
  
6.  Zlokalizuj `Class` instrukcji, `Partial Public Class ValueButton`i zmienić typ, z której dziedziczy ten formant <xref:System.Windows.Forms.UserControl> do <xref:System.Windows.Forms.Button>. Dzięki temu dziedziczone formantu dziedziczy wszystkie funkcje <xref:System.Windows.Forms.Button> formantu.  
  
7.  Zlokalizuj `InitializeComponent` — metoda i Usuń wiersz, który przypisuje <xref:System.Windows.Forms.ContainerControl.AutoScaleMode%2A> właściwości. Ta właściwość nie istnieje w <xref:System.Windows.Forms.Button> formantu.  
  
8.  Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.  
  
     Należy pamiętać, że projektant wizualny nie jest już dostępny. Ponieważ <xref:System.Windows.Forms.Button> formant wykonuje własny obraz, nie można zmodyfikować jego wygląd w projektancie. Jego wizualnej reprezentacji będą dokładnie taka sama jak klasa dziedziczy z (czyli <xref:System.Windows.Forms.Button>), chyba że zmodyfikowany w kodzie.  
  
> [!NOTE]
>  Nadal możesz dodać składniki, które mają żadnych elementów interfejsu użytkownika, na powierzchnię projektu.  
  
## <a name="adding-a-property-to-your-inherited-control"></a>Dodawanie właściwości do dziedziczonej formantu  
 Jeden wykorzystanie dziedziczone formanty formularzy systemu Windows jest tworzenie formantów, które są takie same jak w wygląd i zachowanie (wygląd i działanie) standardowe formanty formularzy systemu Windows, ale udostępniają właściwości niestandardowych. W tej sekcji dodasz właściwość o nazwie `ButtonValue` do formantu.  
  
#### <a name="to-add-the-value-property"></a>Aby dodać właściwości Value  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **ValueButton.vb**, a następnie kliknij przycisk **kod widoku** z menu skrótów.  
  
2.  Zlokalizuj `Public Class ValueButton` instrukcji. Natychmiast poniżej tej instrukcji, wpisz następujący kod:  
  
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
  
     Ten kod ustawia metody za pomocą której `ButtonValue` przechowywania i pobierania właściwości. `Get` Instrukcja ustawia wartości zwracanej wartości, który jest przechowywany w prywatnej zmiennej `varValue`i `Set` instrukcja ustawia wartość zmiennej prywatnej przy użyciu `Value` — słowo kluczowe.  
  
3.  Z **pliku** menu, wybierz **Zapisz wszystko** zapisać projektu.  
  
## <a name="testing-your-control"></a>Testowanie formantu  
 Formanty nie są autonomicznych projektów; muszą one być obsługiwane w kontenerze. W celu przetestowania formantu, należy podać projekt testowy na jej uruchamianie. Należy również upewnić formantu dostępne dla projektu testowego według budynków (Kompilacja) go. W tej sekcji zostanie kompilacji formantu i przetestować go w formularzu systemu Windows.  
  
#### <a name="to-build-your-control"></a>Tworzenie formantu  
  
1.  Na **kompilacji** menu, kliknij przycisk **Kompiluj rozwiązanie**.  
  
     Kompilacja zostanie pomyślnie zakończona bez błędów lub ostrzeżeń.  
  
#### <a name="to-create-a-test-project"></a>Aby utworzyć projekt testowy  
  
1.  Na **pliku** menu wskaż **Dodaj** , a następnie kliknij przycisk **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.  
  
2.  Wybierz węzeł projekty Visual Basic, a następnie kliknij przycisk **aplikacji Windows Forms**.  
  
3.  W **nazwa** wpisz `Test`.  
  
4.  W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.  
  
5.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **odwołania** węzła dla projektu testowego, następnie wybierz **Dodaj odwołanie** z menu skrótów do wyświetlenia  **Dodaj odwołanie** okno dialogowe.  
  
6.  Kliknij przycisk **projekty** kartę.  
  
7.  Kliknij kartę **projekty**. Twoje `ValueButtonLib` projektu zostaną wyświetlone w obszarze **Nazwa projektu**. Kliknij dwukrotnie plik projektu można dodać odwołania do projektu testowego.  
  
8.  W **Eksploratora rozwiązań** kliknij prawym przyciskiem myszy **testu** i wybierz **kompilacji**.  
  
#### <a name="to-add-your-control-to-the-form"></a>Aby dodać formantu do formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1.vb** i wybierz polecenie **Widok projektanta** z menu skrótów.  
  
2.  W **przybornika**, kliknij przycisk **składniki ValueButtonLib**. Kliknij dwukrotnie **ValueButton**.  
  
     A **ValueButton** w formularzu.  
  
3.  Kliknij prawym przyciskiem myszy **ValueButton** i wybierz **właściwości** z menu skrótów.  
  
4.  W **właściwości** okna, sprawdź właściwości tego formantu. Należy pamiętać, są takie same jak właściwości udostępniane przez przycisk standardowy, z tą różnicą, że jest właściwością dodatkowe `ButtonValue`.  
  
5.  Ustaw `ButtonValue` właściwości `5`.  
  
6.  Na **wszystkich formularzy systemu Windows** karcie **przybornika**, kliknij dwukrotnie **etykiety** można dodać <xref:System.Windows.Forms.Label> sterowania do formularza.  
  
7.  Przemieszczenie etykietę do Centrum formularza.  
  
8.  Kliknij dwukrotnie `ValueButton1`.  
  
     **Edytora kodu** otwiera `ValueButton1_Click` zdarzeń.  
  
9. Wpisz następujący wiersz kodu.  
  
    ```vb  
    Label1.Text = CStr(ValueButton1.ButtonValue)  
    ```  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **testu**i wybierz polecenie **Ustaw jako projekt startowy** z menu skrótów.  
  
11. Z **debugowania** menu, wybierz opcję **Rozpocznij debugowanie**.  
  
     `Form1` zostanie wyświetlone.  
  
12. Kliknij przycisk `Valuebutton1`.  
  
     Liczb, "5" jest wyświetlany w `Label1`, ilustrujące który `ButtonValue` właściwości dziedziczone formantu został przekazany do `Label1` za pośrednictwem `ValueButton1_Click` metody. W związku z tym Twoje `ValueButton` kontrola dziedziczy wszystkie funkcje standardowej przycisku formularzy systemu Windows, ale udostępnia dodatkowe, niestandardowe właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik: tworzenie kontrolki złożonej za pomocą języka Visual Basic](../../../../docs/framework/winforms/controls/walkthrough-authoring-a-composite-control-with-visual-basic.md)  
 [Instrukcje: wyświetlanie kontrolki w oknie dialogowym Wybierz elementy przybornika](../../../../docs/framework/winforms/controls/how-to-display-a-control-in-the-choose-toolbox-items-dialog-box.md)  
 [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [Podstawowe informacje o dziedziczeniu (Visual Basic)](~/docs/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [Wskazówki dotyczące tworzenia składników](http://msdn.microsoft.com/library/c414cca9-2489-4208-8b38-954586d91c13)
