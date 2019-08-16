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
ms.openlocfilehash: 6fd504269ae9afbfd02b58276582a644674e1e0f
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69040324"
---
# <a name="walkthrough-demonstrating-visual-inheritance"></a>Przewodnik: Demonstrowanie dziedziczenia Visual

Dziedziczenie wizualne umożliwia wyświetlanie kontrolek w formularzu podstawowym i dodawanie nowych kontrolek. W tym instruktażu utworzysz formularz podstawowy i skompilujesz go w bibliotece klas. Ta biblioteka klas zostanie zaimportowana do innego projektu i zostanie utworzony nowy formularz, który dziedziczy po formularzu podstawowym. W tym instruktażu dowiesz się, jak:

- Utwórz projekt biblioteki klas zawierający formularz podstawowy.

- Dodaj przycisk z właściwościami, które mogą modyfikować klasy pochodne formularza podstawowego.

- Dodaj przycisk, którego nie można modyfikować przez dziedziczenie formularza podstawowego.

- Utwórz projekt zawierający formularz, który dziedziczy z `BaseForm`.

W tym instruktażu przedstawiono różnicę między kontrolkami prywatnymi i chronionymi w formularzu dziedziczonym.

> [!CAUTION]
> Nie wszystkie formanty obsługują dziedziczenie wizualne z formularza podstawowego. Następujące kontrolki nie obsługują scenariusza opisanego w tym instruktażu:
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
>  Te kontrolki w dziedziczonym formularzu są zawsze tylko do odczytu, niezależnie od używanej modyfikatora (`private`, `protected`lub `public`).

## <a name="create-a-class-library-project-containing-a-base-form"></a>Tworzenie projektu biblioteki klas zawierającego formularz podstawowy

1. W programie Visual Studio w menu **plik** wybierz polecenie **Nowy** > **projekt** , aby otworzyć okno dialogowe **Nowy projekt** .

2. Utwórz aplikację Windows Formsową o `BaseFormLibrary`nazwie.

3. Aby utworzyć bibliotekę klas zamiast standardowej aplikacji Windows Forms, w **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy węzeł projektu **BaseFormLibrary** , a następnie wybierz polecenie **Właściwości**.

4. We właściwościach projektu Zmień **Typ danych wyjściowych** z **aplikacji systemu Windows** na **bibliotekę klas**.

5. Z menu **plik** wybierz polecenie **Zapisz wszystko** , aby zapisać projekt i pliki w domyślnej lokalizacji.

 Dwie następne procedury umożliwiają dodanie przycisków do formularza podstawowego. Aby zademonstrować dziedziczenie wizualne, nadajesz przyciskom różne poziomy dostępu `Modifiers` , ustawiając ich właściwości.

## <a name="add-a-button-that-inheritors-of-the-base-form-can-modify"></a>Dodaj przycisk, który może modyfikować dziedziczenie formularza podstawowego

1. Otwórz **formularz Form1** w projektancie.

2. Na karcie **wszystkie Windows Forms** przybornika kliknijdwukrotnie przycisk, aby dodać przycisk do formularza. Użyj myszy, aby ustawić położenie przycisku i zmienić jego rozmiar.

3. W okno Właściwości ustaw następujące właściwości przycisku:

    - Ustaw właściwość **Text** , aby **powiedzieć Hello**.

    - Ustaw właściwość **(Name)** na **btnProtected**.

    - Ustaw właściwość **Modyfikatory** na wartość **Protected**. Dzięki temu formularze dziedziczące z **formularza Form1** są modyfikowane w celu zmodyfikowania właściwości **btnProtected**.

4. Kliknij dwukrotnie przycisk **powiedz Hello** , aby dodać procedurę obsługi zdarzeń dla zdarzenia **kliknięcia** .

5. Dodaj następujący wiersz kodu do programu obsługi zdarzeń:

    ```vb
    MessageBox.Show("Hello, World!")
    ```

    ```csharp
    MessageBox.Show("Hello, World!");
    ```

## <a name="add-a-button-that-cannot-be-modified-by-inheritors-of-the-base-form"></a>Dodaj przycisk, którego nie można modyfikować przez dziedziczenie formularza podstawowego

1. Przejdź do widoku projektu, klikając kartę **Form1. vb [projekt], Form1.cs [Design] lub Form1. JSL [Design]** nad edytorem kodu lub naciskając klawisz F7.

2. Dodaj drugi przycisk i ustaw jego właściwości w następujący sposób:

    - Ustaw właściwość **Text** na wartość"Pożegnanie".

    - Ustaw właściwość **(Name)** na **btnPrivate**.

    - Ustaw właściwość **Modyfikatory** na wartość **Private**. To sprawia, że dla formularzy dziedziczących z **formularza Form1** nie można modyfikować właściwości **btnPrivate**.

3. Kliknij dwukrotnie przycisk "na **przykład** ", aby dodać procedurę obsługi zdarzeń dla zdarzenia **kliknięcia** . W procedurze zdarzenia umieść następujący wiersz kodu:

    ```vb
    MessageBox.Show("Goodbye!")
    ```

    ```csharp
    MessageBox.Show("Goodbye!");
    ```

4. Z menu **kompilacja** wybierz kolejno opcje **Kompiluj BaseForm Library** , aby skompilować bibliotekę klas.

     Po skompilowaniu biblioteki można utworzyć nowy projekt, który dziedziczy po właśnie utworzonym formularzu.

## <a name="create-a-project-containing-a-form-that-inherits-from-the-base-form"></a>Utwórz projekt zawierający formularz, który dziedziczy z formularza podstawowego

1. Z menu **plik** wybierz polecenie **Dodaj** , a następnie **Nowy projekt** , aby otworzyć okno dialogowe **Dodaj nowy projekt** .

2. Utwórz aplikację Windows Formsową o `InheritanceTest`nazwie.

## <a name="add-an-inherited-form"></a>Dodaj Dziedziczony formularz

1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** , wybierz polecenie **Dodaj**, a następnie wybierz pozycję **nowy element**.

2. W oknie dialogowym **Dodaj nowy element** wybierz kategorię **Windows Forms** (Jeśli masz listę kategorii), a następnie wybierz **Dziedziczony szablon formularza** .

3. Pozostaw domyślną nazwę `Form2` , a następnie kliknij przycisk **Dodaj**.

4. W oknie dialogowym **Selektor dziedziczenia** wybierz opcję **Form1** z projektu **BaseFormLibrary** jako formularz do dziedziczenia, a następnie kliknij przycisk **OK**.

     Spowoduje to utworzenie formularza w projekcie **InheritanceTest** , który pochodzi z formularza w **BaseFormLibrary**.

5. Otwórz Dziedziczony formularz (**Form2**) w projektancie, klikając go dwukrotnie, jeśli nie jest jeszcze otwarty.

     W projektancie przyciski dziedziczone mają symbol (![Zrzut ekranu przedstawiający symbol dziedziczenia Visual Basic.](./media/walkthrough-demonstrating-visual-inheritance/visual-basic-inheritance-glyph.gif)) w górnym rogu wskazujące, że są dziedziczone.

6. Wybierz przycisk **powiedz Hello** i obserwuj uchwyty zmiany rozmiaru. Ponieważ ten przycisk jest chroniony, dziedziczenia można przenieść, zmienić jego rozmiar, zmienić jego podpis i wprowadzić inne modyfikacje.

7. Wybierz prywatny przycisk "Pożegnanie" i zwróć uwagę, że nie ma dojść do zmiany rozmiaru. Ponadto w oknie **Właściwości** właściwości tego przycisku są wyszarzone, aby wskazać, że nie można ich modyfikować.

8. Jeśli używasz wizualizacji C#:

    1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy pozycję **Form1** w projekcie **InheritanceTest** , a następnie wybierz polecenie **Usuń**. W wyświetlonym oknie komunikatu kliknij przycisk **OK** , aby potwierdzić usunięcie.

    2. Otwórz plik program.cs i Zmień wiersz `Application.Run(new Form1());` na. `Application.Run(new Form2());`

9. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** i wybierz pozycję **Ustaw jako projekt startowy**.

10. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt **InheritanceTest** i wybierz polecenie **Właściwości**.

11. Na stronach właściwości **InheritanceTest** Ustaw **obiekt startowy** jako Dziedziczony formularz (**Form2**).

12. Naciśnij klawisz **F5** , aby uruchomić aplikację, i obserwuj zachowanie dziedziczonego formularza.

## <a name="next-steps"></a>Następne kroki

Dziedziczenie dla kontrolek użytkownika działa w podobny sposób. Otwórz nowy projekt biblioteki klas i Dodaj kontrolkę użytkownika. Umieść w nim kontrolki elementów i skompiluj projekt. Otwórz inny projekt biblioteki klas i Dodaj odwołanie do skompilowanej biblioteki klas. Ponadto spróbuj dodać odziedziczony formant (za pomocą okna dialogowego **Dodaj nowe elementy** ) do projektu i przy użyciu **selektora dziedziczenia**. Dodaj kontrolkę użytkownika i Zmień `Inherits` instrukcję (`:` w języku wizualnym C#). Aby uzyskać więcej informacji, zobacz [jak: Dziedzicz Windows Forms](how-to-inherit-windows-forms.md).

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Dziedzicz Windows Forms](how-to-inherit-windows-forms.md)
- [Formularze Windows Forms — dziedziczenie wizualizacji](windows-forms-visual-inheritance.md)
- [Windows Forms](../index.md)
