---
title: przechowywanie obiektu w programie Visual Studio
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: fbd342c929e8519571c0f6bb76d4091efcfe4476
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350396"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Przewodnik: utrwalanie obiektu w programie Visual Studio (Visual Basic)
Chociaż właściwości obiektu można ustawić na wartości domyślne w czasie projektowania, wszelkie wartości wprowadzone w czasie wykonywania są tracone, gdy obiekt zostanie zniszczony. Możesz użyć serializacji, aby zachować dane obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym utworzeniu wystąpienia obiektu.  
  
> [!NOTE]
> W Visual Basic, aby przechowywać proste dane, takie jak nazwa lub liczba, można użyć obiektu `My.Settings`. Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 W tym instruktażu utworzysz prosty obiekt `Loan` i zachowasz jego dane do pliku. Następnie dane zostaną pobrane z pliku po ponownym utworzeniu obiektu.  
  
> [!IMPORTANT]
> Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje. Jeśli aplikacja musi utworzyć plik, aplikacja musi `Create` uprawnienie dla tego folderu. Uprawnienia są ustawiane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja wymaga tylko `Write` uprawnienia, ale jest to małe uprawnienie. Jeśli to możliwe, bezpieczniejsze jest tworzenie pliku podczas wdrażania i udzielanie uprawnień `Read` tylko do jednego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder Program Files.  
  
> [!IMPORTANT]
> Ten przykład zapisuje dane w postaci binarnej. Tych formatów nie należy używać w przypadku poufnych danych, takich jak hasła lub informacje o kartach kredytowych.  
  
> [!NOTE]
> Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Importuj i Eksportuj ustawienia** w menu **Narzędzia** . Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczek  
 Pierwszym krokiem jest utworzenie klasy `Loan` i aplikacji testowej, która używa klasy.  
  
### <a name="to-create-the-loan-class"></a>Aby utworzyć klasę pożyczek  
  
1. Utwórz nowy projekt biblioteki klas i nadaj mu nazwę "LoanClass". Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań i projektów](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2. W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku Class1 i wybierz polecenie **Zmień nazwę**. Zmień nazwę pliku na `Loan` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `Loan`.  
  
3. Dodaj następujące publiczne elementy członkowskie do klasy:  
  
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
  
 Należy również utworzyć prostą aplikację, która używa klasy `Loan`.  
  
### <a name="to-create-a-test-application"></a>Aby utworzyć aplikację testową  
  
1. Aby dodać projekt aplikacji Windows Forms do rozwiązania, w menu **plik** wybierz polecenie **Dodaj**,**Nowy projekt**.  
  
2. W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **Windows Forms aplikacja**, a następnie wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
3. W **Eksplorator rozwiązań**wybierz projekt LoanApp.  
  
4. W menu **projekt** wybierz pozycję **Ustaw jako projekt startowy**.  
  
5. W menu **projekt** wybierz polecenie **Dodaj odwołanie**.  
  
6. W oknie dialogowym **Dodaj odwołanie** wybierz kartę **projekty** , a następnie wybierz projekt LoanClass.  
  
7. Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
8. W projektancie Dodaj cztery <xref:System.Windows.Forms.TextBox> kontrolki do formularza.  
  
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
  
10. Dodaj procedurę obsługi zdarzeń dla zdarzenia `PropertyChanged` do formularza przy użyciu następującego kodu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 W tym momencie można skompilować i uruchomić aplikację. Należy zauważyć, że wartości domyślne z klasy `Loan` pojawiają się w polach tekstowych. Spróbuj zmienić wartość stopy oprocentowania z 7,5 na 7,1, a następnie zamknij aplikację i uruchom ją ponownie — wartość zostanie przywrócona do wartości domyślnej 7,5.  
  
 W świecie rzeczywistym stawki odsetek zmieniają się okresowo, ale nie zawsze, gdy aplikacja jest uruchomiona. Zamiast sprawiać, że użytkownik nie aktualizuje stopy oprocentowania za każdym razem, gdy aplikacja jest uruchomiona, lepiej jest zachować najnowszą stawkę odsetek między wystąpieniami aplikacji. W następnym kroku wystarczy dodać serializację do klasy pożyczek.  
  
## <a name="using-serialization-to-persist-the-object"></a>Utrwalanie obiektu przy użyciu serializacji  
 Aby zachować wartości dla klasy pożyczek, należy najpierw oznaczyć klasę atrybutem `Serializable`.  
  
### <a name="to-mark-a-class-as-serializable"></a>Aby oznaczyć klasę jako możliwy do serializacji  
  
- Zmień deklarację klasy dla klasy pożyczek w następujący sposób:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 Atrybut `Serializable` informuje kompilator, że wszystkie elementy w klasie mogą być utrwalane w pliku. Ponieważ zdarzenie `PropertyChanged` jest obsługiwane przez obiekt formularza systemu Windows, nie może być serializowane. Atrybut `NonSerialized` może służyć do oznaczania elementów członkowskich klasy, które nie powinny być utrwalane.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Aby zapobiec serializacji elementu członkowskiego  
  
- Zmień deklarację dla zdarzenia `PropertyChanged` w następujący sposób:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp. Aby serializować klasę i zapisać ją do pliku, należy użyć przestrzeni nazw <xref:System.IO> i <xref:System.Xml.Serialization>. Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych bibliotek klas.  
  
### <a name="to-add-references-to-namespaces"></a>Aby dodać odwołania do przestrzeni nazw  
  
- Dodaj następujące instrukcje na początku klasy `Form1`:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     W takim przypadku używasz pliku binarnego programu formatującego do zapisania obiektu w formacie binarnym.  
  
 Następnym krokiem jest dodanie kodu w celu deserializacji obiektu z pliku po utworzeniu obiektu.  
  
### <a name="to-deserialize-an-object"></a>Do deserializacji obiektu  
  
1. Dodaj stałą do klasy dla nazwy pliku serializowanej danych.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. Zmodyfikuj kod w procedurze zdarzenia `Form1_Load` w następujący sposób:  
  
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
  
     Należy pamiętać, że najpierw należy sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz klasę <xref:System.IO.Stream>, aby odczytać plik binarny i klasę <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>, aby przetłumaczyć plik. Należy również przekonwertować typ strumienia na typ obiektu pożyczki.  
  
 Następnie musisz dodać kod, aby zapisać dane wprowadzone w polach tekstowych do klasy `Loan`, a następnie trzeba serializować klasy do pliku.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Aby zapisać dane i serializować klasę  
  
- Dodaj następujący kod do procedury zdarzenia `Form1_FormClosing`:  
  
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
  
 W tym momencie możesz ponownie skompilować i uruchomić aplikację. Początkowo wartości domyślne pojawiają się w polach tekstowych. Spróbuj zmienić wartości i wprowadź nazwę w czwartym polu tekstowym. Zamknij aplikację, a następnie uruchom ją ponownie. Należy pamiętać, że nowe wartości są teraz wyświetlane w polach tekstowych.  
  
## <a name="see-also"></a>Zobacz także

- [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [Przewodnik programowania Visual Basic](../../../../visual-basic/programming-guide/index.md)
