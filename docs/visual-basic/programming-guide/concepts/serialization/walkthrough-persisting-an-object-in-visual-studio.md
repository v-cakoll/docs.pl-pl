---
title: Przechowywanie obiektu w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 55ad2049003baaed26f4db909ae466aefdd161e1
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59303352"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Przewodnik: Przechowywanie obiektu w programie Visual Studio (Visual Basic)
Chociaż można ustawić właściwości obiektu do wartości domyślnych w czasie projektowania, wszystkie wartości wprowadzone w czasie wykonywania zostaną utracone, kiedy niszczony jest obiekt. Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, dzięki czemu możesz przechowywać wartości, a następnie pobrać jednego z nich przy następnym uruchomieniu jest tworzone wystąpienie obiektu.  
  
> [!NOTE]
>  W Visual Basic do przechowywania danych proste, takie jak nazwa lub numer, można użyć `My.Settings` obiektu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 W tym instruktażu utworzysz prostą `Loan` obiekt i utrwala jego dane do pliku. Następnie powoduje pobranie danych z pliku, gdy ponownie utworzyć obiekt.  
  
> [!IMPORTANT]
>  W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi `Create` uprawnienie do tego folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` uprawnienia, mniejsze uprawnienia. Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub do folderu Program Files.  
  
> [!IMPORTANT]
>  W tym przykładzie przechowuje dane w pliku binarnym. Nie można używać tych formatów poufnych danych, takie jak hasła lub informacji o karcie kredytowej.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki  
 Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja testowa, która używa klasy.  
  
### <a name="to-create-the-loan-class"></a>Aby utworzyć klasę pożyczki  
  
1. Utwórz nowy projekt biblioteki klas i nadaj mu nazwę "LoanClass". Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2. W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku Class1 i wybierz **Zmień nazwę**. Zmień nazwę pliku do `Loan` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `Loan`.  
  
3. Dodaj następujące składowe publiczne klasy:  
  
    ```vb  
    Public Class Loan  
        Implements System.ComponentModel.INotifyPropertyChanged  
  
        Public Property LoanAmount As Double  
        Public Property InterestRate As Double  
        Public Property Term As Integer  
  
        Private p_Customer As String  
        Public Property Customer As String  
            Get  
                Return p_Customer  
            End Get  
            Set(ByVal value As String)  
                p_Customer = value  
                RaiseEvent PropertyChanged(Me,  
                  New System.ComponentModel.PropertyChangedEventArgs("Customer"))  
            End Set  
        End Property  
  
        Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
          Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
  
        Public Sub New(ByVal loanAmount As Double,  
                       ByVal interestRate As Double,  
                       ByVal term As Integer,  
                       ByVal customer As String)  
  
            Me.LoanAmount = loanAmount  
            Me.InterestRate = interestRate  
            Me.Term = term  
            p_Customer = customer  
        End Sub  
    End Class  
    ```  
  
 Ponadto trzeba będzie utworzyć prostą aplikację, która używa `Loan` klasy.  
  
### <a name="to-create-a-test-application"></a>Aby utworzyć aplikację testu  
  
1. Aby dodać projekt aplikacja interfejsu Windows Forms do rozwiązania, na **pliku** menu, wybierz **Dodaj**,**nowy projekt**.  
  
2. W **Dodaj nowy projekt** okna dialogowego wybierz **aplikacja interfejsu Windows Forms**, a następnie wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe .  
  
3. W **Eksploratora rozwiązań**, wybierz projekt LoanApp.  
  
4. Na **projektu** menu, wybierz **Ustaw jako projekt startowy**.  
  
5. Na **projektu** menu, wybierz **Dodaj odwołanie**.  
  
6. W **Dodaj odwołanie** okna dialogowego wybierz **projektów** kartę, a następnie wybierz projekt LoanClass.  
  
7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
8. W projektancie, dodaj cztery <xref:System.Windows.Forms.TextBox> formantów do formularza.  
  
9. W Edytorze kodu dodaj następujący kod:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. Dodawanie obsługi zdarzeń dla `PropertyChanged` zdarzeń do formularza przy użyciu następującego kodu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 W tym momencie można tworzyć i uruchomić aplikację. Należy zauważyć, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych. Spróbuj zmienić wartość stopy z 7,5 na 7.1, zamknij aplikację i ponownie uruchom — przywraca wartość domyślną w wersji 7.5.  
  
 W świecie rzeczywistym oprocentowania zmienić okresowo, ale niekoniecznie każdorazowym uruchomieniu aplikacji. Zamiast wprowadzania użytkownika zaktualizować stopę każdorazowym uruchomieniu aplikacji, lepiej jest zapewnienie najnowszych stopie między wystąpieniami aplikacji. W następnym kroku będziesz robić to dodając serializacji do klasy pożyczki.  
  
## <a name="using-serialization-to-persist-the-object"></a>Za pomocą serializacji, aby utrwalić obiektu  
 Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę za pomocą `Serializable` atrybutu.  
  
### <a name="to-mark-a-class-as-serializable"></a>Aby oznaczyć klasę jako możliwe do serializacji  
  
-   Zmień deklarację klasy dla klasy pożyczek w następujący sposób:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Atrybut informuje kompilator, że wszystkie elementy w klasie mogą zostać utrwalone w pliku. Ponieważ `PropertyChanged` zdarzenie jest obsługiwane przez obiekt formularza Windows, nie może być serializowany. `NonSerialized` Atrybut może służyć do oznaczania składowych klasy, które nie powinny zostać utrwalone.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Aby zapobiec elementu członkowskiego serializowanego  
  
-   Zmienianie deklaracji pod kątem `PropertyChanged` zdarzeń w następujący sposób:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Następnym krokiem jest dodać kod serializacji do aplikacji LoanApp. Aby można było serializować klasy i zapisze go w pliku, użyjesz <xref:System.IO> i <xref:System.Xml.Serialization> przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do bibliotek klas niezbędne.  
  
### <a name="to-add-references-to-namespaces"></a>Aby dodać odwołania do przestrzeni nazw  
  
-   Dodaj następujące instrukcje na górze `Form1` klasy:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     W tym przypadku używasz binarny program formatujący pozwala zapisać obiekt w formacie binarnym.  
  
 Następnym krokiem jest dodawanie kodu do deserializacji obiektu na podstawie pliku, gdy obiekt zostanie utworzony.  
  
### <a name="to-deserialize-an-object"></a>Do deserializacji obiektu  
  
1. Dodaj stałą do klasy dla nazwy pliku serializowane dane.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. Zmodyfikuj kod `Form1_Load` procedury zdarzenia w następujący sposób:  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        If File.Exists(FileName) Then  
            Dim TestFileStream As Stream = File.OpenRead(FileName)  
            Dim deserializer As New BinaryFormatter  
            TestLoan = CType(deserializer.Deserialize(TestFileStream), LoanClass.Loan)  
            TestFileStream.Close()  
        End If  
  
        AddHandler TestLoan.PropertyChanged, AddressOf Me.CustomerPropertyChanged  
  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
     Pamiętaj, że najpierw należy sprawdzić czy plik istnieje. Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy można odczytać pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku. Należy również konwersji z typu strumienia do typu obiektu pożyczki.  
  
 Następnie należy dodać kod, aby zapisać dane wprowadzone w polach tekstowych do `Loan` klasy, a następnie muszą serializację klasy w pliku.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Aby zapisać dane i serializacji klasę  
  
-   Dodaj następujący kod do `Form1_FormClosing` procedury zdarzenia:  
  
    ```vb  
    Private Sub Form1_FormClosing() Handles MyBase.FormClosing  
        TestLoan.LoanAmount = CDbl(TextBox1.Text)  
        TestLoan.InterestRate = CDbl(TextBox2.Text)  
        TestLoan.Term = CInt(TextBox3.Text)  
        TestLoan.Customer = TextBox4.Text  
  
        Dim TestFileStream As Stream = File.Create(FileName)  
        Dim serializer As New BinaryFormatter  
        serializer.Serialize(TestFileStream, TestLoan)  
        TestFileStream.Close()  
    End Sub  
    ```  
  
 W tym momencie możesz ponownie skompiluj i uruchom aplikację. Początkowo wartości domyślne są wyświetlane w polach tekstowych. Spróbuj zmienić wartości i wprowadź nazwę w polu tekstowym czwarty. Zamknij aplikację, a następnie uruchom ją ponownie. Pamiętaj, że pojawiają się nowe wartości w polach tekstowych.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Przewodnik programowania w Visual Basic](../../../../visual-basic/programming-guide/index.md)
