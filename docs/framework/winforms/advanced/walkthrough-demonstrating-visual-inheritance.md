---
title: 'Wskazówki: demonstrowanie dziedziczenia Visual'
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
ms.openlocfilehash: 61239d9b547be73a14618d41feeb9aeea9f8ded6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33529704"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Wskazówki: demonstrowanie dziedziczenia Visual
Dziedziczenie Visual umożliwia sprawdzenie kontrolek w formularzu podstawowej i dodać nowe kontrolki. W tym przewodniku utworzysz formularza podstawowego i skompiluj go do biblioteki klas. Zostanie zaimportować tę bibliotekę klas do innego projektu i Utwórz nowy formularz, który dziedziczy z formularza podstawowego. W tym przewodniku przedstawiono sposób:  
  
-   Tworzenie projektu biblioteki klas, zawierający formularz podstawowy.  
  
-   Dodaj przycisk Właściwości, które pochodzi z klasy podstawowej formularza można modyfikować.  
  
-   Dodawanie przycisku, który nie może modyfikować dziedziczenia formularza podstawowego.  
  
-   Utwórz projekt zawierający formularz, który dziedziczy `BaseForm`.  
  
 Ostatecznie w tym przewodniku zostaną przedstawione różnica między prywatnych i chronionych formantów w formularzu dziedziczone.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
> [!CAUTION]
>  Nie wszystkie formanty obsługuje dziedziczenie visual z formularz podstawowy. Następujące formanty nie obsługują scenariusz opisany w tym przewodniku:  
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
>  Tych kontrolek w formularzu dziedziczone są zawsze, niezależnie od Modyfikatory używany jest tylko do odczytu (`private`, `protected`, lub `public`).  
  
## <a name="scenario-steps"></a>Kroki w scenariuszu  
 Pierwszym krokiem jest tworzenie formularza podstawowego.  
  
#### <a name="to-create-a-class-library-project-containing-a-base-form"></a>Aby utworzyć projektu biblioteki klas, zawierający formularza podstawowego  
  
1.  Z **pliku** menu, wybierz **nowy**, a następnie **projektu** otworzyć **nowy projekt** okno dialogowe.  
  
2.  Tworzenie aplikacji formularzy systemu Windows o nazwie `BaseFormLibrary`.  
  
3.  Do tworzenia biblioteki klas zamiast standardowego aplikacji formularzy systemu Windows, w **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **BaseFormLibrary** węzła projektu, a następnie wybierz **właściwości**.  
  
4.  We właściwościach projektu, należy zmienić **Output typu** z **aplikacji systemu Windows** do **biblioteki klas**.  
  
5.  Z **pliku** menu, wybierz **Zapisz wszystko** do zapisywania plików projektu i w lokalizacji domyślnej.  
  
 Procedury w dwóch następnych dodawanie przycisków do formularza podstawowego. Aby zademonstrować dziedziczenie visual, klient będzie przekazywać przycisków różne poziomy dostępu przez ustawienie ich `Modifiers` właściwości.  
  
#### <a name="to-add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Aby dodać przycisku, który można modyfikować dziedziczenia formularza podstawowego  
  
1.  Otwórz **Form1** w projektancie.  
  
2.  Na **wszystkich formularzy systemu Windows** karcie **przybornika**, kliknij dwukrotnie **przycisk** w celu dodania przycisku do formularza. Za pomocą myszy pozycji, a następnie zmień rozmiar przycisku.  
  
3.  W oknie właściwości ustaw następujące właściwości przycisku:  
  
    -   Ustaw **tekst** właściwości **Hello powiedzieć**.  
  
    -   Ustaw **(nazwa)** właściwości **btnProtected**.  
  
    -   Ustaw**Modyfikatory** właściwości **chronione**. Dzięki temu formularze, które dziedziczą z **Form1** można zmodyfikować właściwości **btnProtected**.  
  
4.  Kliknij dwukrotnie **Hello powiedzieć** przycisk, aby dodać obsługę zdarzeń dla **kliknij** zdarzeń.  
  
5.  Dodaj następujący wiersz kodu do obsługi zdarzeń:  
  
    ```vb  
    MessageBox.Show("Hello, World!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Hello, World!");  
    ```  
  
#### <a name="to-add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Aby dodać przycisk, którego nie można zmodyfikować przez dziedziczenia formularza podstawowego  
  
1.  Przełącz do widoku projektu, klikając **Form1.vb [projekt], [projekt] pliku Form1.cs lub Form1.jsl [projekt]** kartę powyżej edytora kodu lub naciskając klawisz F7.  
  
2.  Dodawanie drugiego przycisku i ustawienia swoich właściwości w następujący sposób:  
  
    -   Ustaw **tekst** właściwości **Goodbye powiedzieć**.  
  
    -   Ustaw **(nazwa)** właściwości **btnPrivate**.  
  
    -   Ustaw **Modyfikatory** właściwości **prywatnej**. Uniemożliwia jej formularze, które dziedziczą z **Form1** można zmodyfikować właściwości **btnPrivate**.  
  
3.  Kliknij dwukrotnie **Goodbye powiedzieć** przycisk, aby dodać obsługę zdarzeń dla **kliknij** zdarzeń. Umieść następujący wiersz kodu w procedurze zdarzenia:  
  
    ```vb  
    MessageBox.Show("Goodbye!")  
    ```  
  
    ```csharp  
    MessageBox.Show("Goodbye!");  
    ```  
  
4.  Z **kompilacji** menu, wybierz **kompilacji biblioteki BaseForm** do tworzenia biblioteki klas.  
  
     Po utworzeniu biblioteki można utworzyć nowy projekt, który dziedziczy z formularza, który został utworzony.  
  
#### <a name="to-create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Aby utworzyć projekt zawierający formularz, który dziedziczy z formularza podstawowego  
  
1.  Z **pliku** menu, wybierz **Dodaj** , a następnie **nowy projekt** otworzyć **Dodawanie nowego projektu** okno dialogowe.  
  
2.  Tworzenie aplikacji formularzy systemu Windows o nazwie `InheritanceTest`.  
  
#### <a name="to-add-an-inherited-form"></a>Aby dodać dziedziczone formularza  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projektu, zaznacz **Dodaj**, a następnie wybierz**nowy element**.  
  
2.  W **Dodaj nowy element** okno dialogowe, wybierz opcję **formularzy systemu Windows** kategorii (Jeśli korzystasz z listy Kategorie), a następnie wybierz **dziedziczone formularza** szablonu.  
  
3.  Pozostaw nazwę domyślną `Form2` , a następnie kliknij przycisk **Dodaj**.  
  
4.  W **selektora dziedziczenia** okno dialogowe, wybierz opcję **Form1** z **BaseFormLibrary** projektu jako formularza, aby dziedziczyć z, a następnie kliknij przycisk **OK** .  
  
     Spowoduje to utworzenie formularza w **InheritanceTest** projektu pochodzący z formularza w **BaseFormLibrary**.  
  
5.  Otwórz formularz dziedziczone (**formularz2**) w projektancie, klikając go, jeśli nie jest już otwarty.  
  
     W Projektancie dziedziczone przyciski mają symbolu (![VisualBasicInheritanceSymbol — zrzut ekranu](../../../../docs/framework/winforms/advanced/media/vbinheritanceglyph.gif "vbInheritanceGlyph")) w górnym rogu, wskazując, są one dziedziczone.  
  
6.  Wybierz **Hello powiedzieć** przycisk i obserwować uchwytów zmiany rozmiaru. Ponieważ ten przycisk jest chroniony, dziedziczenia można go przenieść, jej rozmiar, zmienić jego podpis i wprowadzić inne zmiany.  
  
7.  Wybierz prywatna **Goodbye powiedzieć** przycisk i zwróć uwagę, że nie ma uchwytów zmiany rozmiaru. Ponadto w **właściwości** okna właściwości tego przycisku jest wyszarzony wskaż, nie może być modyfikowany.  
  
8.  Jeśli używasz programu Visual C#:  
  
    1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **Form1** w **InheritanceTest** projektu, a następnie wybierz pozycję **usunąć**. W wyświetlonym oknie komunikatu kliknij **OK** aby potwierdzić usunięcie.  
  
    2.  Otwórz plik Program.cs i zmień wiersz `Application.Run(new Form1());` do `Application.Run(new Form2());`.  
  
9. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projekt i wybierz **Ustaw jako projekt startowy**.  
  
10. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy **InheritanceTest** projekt i wybierz **właściwości**.  
  
11. W **InheritanceTest** ustawić strony właściwości **obiekt uruchomieniowy** być dziedziczone formularza (**formularz2**).  
  
12. Naciśnij klawisz F5, aby uruchomić aplikację i przyjrzeć się zachowaniu dziedziczone formularza.  
  
## <a name="next-steps"></a>Następne kroki  
 W przypadku kontrolek użytkownika dziedziczenia w podobny sposób. Otwórz nowy projektu biblioteki klas i Dodaj kontrolkę użytkownika. Umieść formanty składników na nim i skompilować projekt. Otwórz innego nowego projektu biblioteki klas i Dodaj odwołanie do biblioteki klas skompilowany. Ponadto spróbuj dodać formant dziedziczony (za pośrednictwem **Dodawanie nowych elementów** okno dialogowe) do projektu i przy użyciu **selektora dziedziczenia**. Dodaj kontrolkę użytkownika, a następnie zmień `Inherits` (`:` języka Visual C#) instrukcji. Aby uzyskać więcej informacji, zobacz [porady: dziedziczenie formularzy systemu Windows](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: dziedziczenie formularzy Windows Forms](../../../../docs/framework/winforms/advanced/how-to-inherit-windows-forms.md)  
 [Formularze Windows Forms — dziedziczenie wizualizacji](../../../../docs/framework/winforms/advanced/windows-forms-visual-inheritance.md)  
 [Windows Forms](../../../../docs/framework/winforms/index.md)
