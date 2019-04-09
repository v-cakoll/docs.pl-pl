---
title: 'Przewodnik: Demonstrowanie dziedziczenia Visual'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- form inheritance [Windows Forms], walkthroughs
- visual inheritance
- inheritance [Windows Forms], walkthroughs
- walkthroughs [Windows Forms], visual inheritance
- Windows Forms, inheritance
ms.assetid: 01966086-3142-450e-8210-3fd4cb33f591
ms.openlocfilehash: 932df915ab55d8141e64836961dd636d3d5da241
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59174606"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Przewodnik: Demonstrowanie dziedziczenia Visual
Dziedziczenie Visual umożliwia sprawdzenie kontrolek w formularzu podstawowej i dodać nowe kontrolki. W tym instruktażu utworzysz formularza podstawowego i skompiluj go do biblioteki klas. Będzie zaimportować tej biblioteki klas do innego projektu i utworzyć nowy formularz, który dziedziczy z formularza podstawowego. Z tego instruktażu dowiesz się jak:  
  
-   Utwórz projekt biblioteki klas zawierający formularz podstawowy.  
  
-   Dodaj przycisk z właściwościami, które pochodne klasy formularza podstawowego można modyfikować.  
  
-   Dodaj przycisk, który nie może modyfikować obiektów dziedziczących z formularza podstawowego.  
  
-   Utwórz projekt zawierający formularz, który dziedziczy z `BaseForm`.  
  
 Ostatecznie w tym instruktażu będą pokazują różnicę między prywatnych i chronionych formantów na odziedziczony formularz.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
> [!CAUTION]
>  Nie wszystkie formanty obsługuje dziedziczenie visual z formularza podstawowego. Następujące elementy sterujące nie obsługują scenariusza opisanego w tym przewodniku:  
>   
>  <xref:System.Windows.Forms.WebBrowser>  
>   
>  <xref:System.Windows.Forms.ToolStrip>  
>   
>  <xref:System.Windows.Forms.ToolStripPanel>  
>   
>  <xref:System.Windows.Forms.TableLayoutPanel>  
>   
>  <xref:System.Windows.Forms.FlowLayoutPanel>  
>   
>  <xref:System.Windows.Forms.DataGridView>  
>   
>  Te kontrolki w odziedziczony formularz są zawsze, niezależnie od tego, Modyfikatory używasz jest tylko do odczytu (`private`, `protected`, lub `public`).  
  
## <a name="scenario-steps"></a>Kroki w scenariuszu  
 Pierwszym krokiem jest utworzyć formularz podstawowy.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Aby utworzyć projekt biblioteki klas zawierający formularza podstawowego  
  
1.  Z **pliku** menu, wybierz **New**, a następnie **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Tworzenie aplikacji Windows Forms o nazwie `BaseFormLibrary`.  
  
3.  Aby utworzyć bibliotekę klas, zamiast do standardowej aplikacji Windows Forms w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **BaseFormLibrary** węzła projektu, a następnie wybierz pozycję **właściwości**.  
  
4.  We właściwościach projektu, należy zmienić **typ danych wyjściowych** z **aplikacji Windows** do **biblioteki klas**.  
  
5.  Z **pliku** menu, wybierz **Zapisz wszystko** do zapisania projektu i plików w lokalizacji domyślnej.  
  
 W dwóch następnych procedur dodać przyciski do formularza podstawowego. Aby zademonstrować dziedziczenie visual, zostanie nadana przyciski różne poziomy dostępu, ustawiając ich `Modifiers` właściwości.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Aby dodać przycisk, który może modyfikować obiektów dziedziczących z formularza podstawowego  
  
1.  Otwórz **Form1** w projektancie.  
  
2.  Na **wszystkie formularze Windows** karcie **przybornika**, kliknij dwukrotnie **przycisk** Aby dodać przycisk do formularza. Aby ustawić położenie i rozmiar przycisku za pomocą myszy.  
  
3.  W oknie właściwości ustaw następujące właściwości przycisku:  
  
    -   Ustaw **tekstu** właściwości **Say Hello**.  
  
    -   Ustaw **(nazwa)** właściwości **btnProtected**.  
  
    -   Ustaw **Modyfikatory** właściwości **chronione**. Dzięki temu możliwe formularzy, które dziedziczą z **Form1** można zmodyfikować właściwości **btnProtected**.  
  
4.  Kliknij dwukrotnie **Say Hello** przycisk, aby dodać moduł obsługi zdarzenia **kliknij** zdarzeń.  
  
5.  Dodaj następujący wiersz kodu do obsługi zdarzeń:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Aby dodać przycisk, który nie może modyfikować obiektów dziedziczących z formularza podstawowego  
  
1.  Przełącz do widoku projektu, klikając pozycję **Form1.vb [projekt], Form1.cs [projekt] lub [projekt] Form1.jsl** kartę powyżej edytora kodu lub naciskając klawisz F7.  
  
2.  Dodaj drugi przycisk i ustaw jego właściwości w następujący sposób:  
  
    -   Ustaw **tekstu** właściwości **Say Goodbye**.  
  
    -   Ustaw **(nazwa)** właściwości **btnPrivate**.  
  
    -   Ustaw **Modyfikatory** właściwości **prywatnej**. Uniemożliwia jej formularzy, które dziedziczą z **Form1** można zmodyfikować właściwości **btnPrivate**.  
  
3.  Kliknij dwukrotnie **Say Goodbye** przycisk, aby dodać moduł obsługi zdarzenia **kliknij** zdarzeń. Umieść następujący wiersz kodu w procedurze zdarzenia:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Z **kompilacji** menu, wybierz **kompilacji biblioteki BaseForm** do tworzenia biblioteki klas.  
  
     Po skompilowaniu biblioteki można utworzyć nowy projekt, który dziedziczy z formularza, który został utworzony.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Aby utworzyć projekt zawierający formularz, który dziedziczy z formularza podstawowego  
  
1.  Z **pliku** menu, wybierz **Dodaj** i następnie **nowy projekt** otworzyć **Dodaj nowy projekt** okno dialogowe.  
  
2.  Tworzenie aplikacji Windows Forms o nazwie `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Aby dodać odziedziczony formularz  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, wybierz opcję **Dodaj**, a następnie wybierz pozycję **nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **Windows Forms** kategorii (Jeśli masz listę kategorii), a następnie wybierz **dziedziczone formularza** szablonu.  
  
3.  Pozostaw domyślną nazwę `Form2` a następnie kliknij przycisk **Dodaj**.  
  
4.  W **selektor dziedziczenia** okno dialogowe, wybierz opcję **Form1** z **BaseFormLibrary** projektu jako formularz, aby dziedziczyć z, a następnie kliknij przycisk **OK** .  
  
     Spowoduje to utworzenie formularza w **InheritanceTest** projektu, który pochodzi z formularza w **BaseFormLibrary**.  
  
5.  Otwórz odziedziczony formularz (**formularz2**) w projektancie, klikając dwukrotnie plik, go, jeśli nie jest już otwarty.  
  
     W Projektancie dziedziczone przyciski powinny mieć symbol (![Zrzut ekranu przedstawiający symbolu dziedziczenie Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) w górnym rogu, wskazując, są one dziedziczone.  
  
6.  Wybierz **Say Hello** przycisk i obserwuj uchwytami zmiany rozmiaru. Ponieważ ten przycisk jest chroniony, obiektów dziedziczących można go przenieść, zmienić jego rozmiar, zmień swój podpis i wprowadzać inne modyfikacje.  
  
7.  Wybierz prywatna **Say Goodbye** przycisku i zwróć uwagę, że nie ma uchwytami zmiany rozmiaru. Ponadto **właściwości** okna właściwości ten przycisk jest wyszarzony do wskazania, nie można ich modyfikować.  
  
8.  Jeśli używasz Visual C#:  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** w **InheritanceTest** projektu, a następnie wybierz **Usuń**. W wyświetlonym oknie komunikatu kliknij **OK** o potwierdzenie usunięcia.  
  
    2.  Otwórz plik Program.cs i zmień wiersz `Application.Run(new Form1());` do `Application.Run(new Form2());`.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, a następnie wybierz **Ustaw jako projekt startowy**.  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, a następnie wybierz **właściwości**.  
  
11. W **InheritanceTest** stron właściwości ustaw **obiekt początkowy** jako odziedziczony formularz (**formularz2**).  
  
12. Naciśnij klawisz F5, aby uruchomić aplikację i przyjrzeć się zachowaniu odziedziczony formularz.  
  
## <a name="next-steps"></a>Następne kroki  
 Dziedziczenie w przypadku kontrolek użytkownika działa w taki sam sposób. Otwórz nowy projekt biblioteki klas i Dodaj kontrolkę użytkownika. Umieść formanty składników na nim i skompiluj projekt. Otwórz inny nowy projekt biblioteki klas i Dodaj odwołanie do biblioteki klas skompilowany. Ponadto spróbuj dodać odziedziczoną kontrolkę (za pośrednictwem **Dodaj nowe elementy** okno dialogowe) do projektu i przy użyciu **selektor dziedziczenia**. Dodaj formant użytkownika, a następnie zmień `Inherits` (`:` w języku Visual C#) instrukcja. Aby uzyskać więcej informacji, zobacz [jak: Dziedziczenie formularzy Windows](how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dziedziczenie formularzy systemu Windows](how-to-inherit-windows-forms.md)
- [Formularze systemu Windows — dziedziczenie Visual](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
