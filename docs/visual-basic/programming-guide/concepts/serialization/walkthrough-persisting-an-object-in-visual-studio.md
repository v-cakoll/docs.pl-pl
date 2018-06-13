---
title: Przechowywanie obiektu w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 2523aefc90e22fe79f22e90d8da68c35c8dd24b0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33655613"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a>Wskazówki: Przechowywanie obiektu w programie Visual Studio (Visual Basic)
Mimo że można ustawić właściwości obiektu do wartości domyślnych w czasie projektowania, wartości wprowadzone w czasie wykonywania zostaną utracone, gdy obiekt zostanie zniszczony. Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, które umożliwia przechowywanie wartości i pobrać je przy następnym uruchomieniu tworzenia wystąpienia obiektu klasy.  
  
> [!NOTE]
>  W języku Visual Basic do przechowywania danych proste, takie jak nazwa lub numer, można użyć `My.Settings` obiektu. Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
 W tym przewodniku, utworzysz prostą `Loan` obiekt i utrwala jego danych do pliku. Następnie zostanie pobrać dane z pliku podczas ponownego tworzenia obiektu.  
  
> [!IMPORTANT]
>  W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi `Create` uprawnienia do tego folderu. Uprawnienia są skonfigurowane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi tylko `Write` uprawnienia, mniejszym uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.  
  
> [!IMPORTANT]
>  W tym przykładzie przechowuje dane w pliku binarnym. Nie można używać tych formatów dla poufnych danych, takie jak hasła lub karty kredytowej.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki  
 Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja testowa, który używa klasy.  
  
### <a name="to-create-the-loan-class"></a>Aby utworzyć klasę pożyczki  
  
1.  Tworzenie nowego projektu biblioteki klas i nadaj jej nazwę na "LoanClass". Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](http://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).  
  
2.  W **Eksploratora rozwiązań**, otwórz plik Class1 menu skrótów i wybierz polecenie **zmienić**. Zmień nazwę pliku do `Loan` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `Loan`.  
  
3.  Dodaj następujące publiczne elementy członkowskie do klasy:  
  
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
  
 Należy także utworzyć prostą aplikację, która używa `Loan` klasy.  
  
### <a name="to-create-a-test-application"></a>Aby utworzyć aplikację testu  
  
1.  Aby dodać projekt aplikacji formularzy systemu Windows do rozwiązania, na **pliku** menu, wybierz **Dodaj**,**nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** oknie dialogowym wybierz **aplikacji Windows Forms**i wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe .  
  
3.  W **Eksploratora rozwiązań**, wybierz projekt LoanApp.  
  
4.  Na **projektu** menu, wybierz **Ustaw jako projekt startowy**.  
  
5.  Na **projektu** menu, wybierz **Dodaj odwołanie**.  
  
6.  W **Dodaj odwołanie** oknie dialogowym wybierz **projekty** karcie, a następnie wybierz projekt LoanClass.  
  
7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
8.  W projektancie, dodaj cztery <xref:System.Windows.Forms.TextBox> formantów w formularzu.  
  
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
  
10. Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzeń do formularza przy użyciu następującego kodu:  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 W tym momencie możesz skompilować i uruchomić aplikację. Należy pamiętać, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych. Zmień wartość stopy z 7.5 7.1, a następnie zamknij aplikację i uruchom go ponownie spróbuj — przywraca wartość domyślną w wersji 7.5.  
  
 W świecie rzeczywistym odsetek zmienić okresowo, ale niekoniecznie każdym uruchomieniu aplikacji. Zamiast wprowadzania użytkownika zaktualizować stopie procentowej zawsze jest uruchomiona aplikacja, zaleca się zachowanie najnowszych stopie procentowej między wystąpieniami aplikacji. W następnym kroku zostanie czy właśnie tę dodając serializacji do klasy pożyczki.  
  
## <a name="using-serialization-to-persist-the-object"></a>Za pomocą serializacji, aby utrwalić obiektu  
 Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę atrybutem `Serializable` atrybutu.  
  
### <a name="to-mark-a-class-as-serializable"></a>Aby oznaczyć klasę jako możliwy do serializacji  
  
-   Zmień deklaracji klasy dla klasy pożyczki w następujący sposób:  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 `Serializable` Atrybut informuje kompilator, że wszystkie elementy w klasie mógł być trwały do pliku. Ponieważ `PropertyChanged` zdarzenie jest obsługiwane przez obiekt formularza systemu Windows, nie można serializować. `NonSerialized` Atrybut może służyć do oznaczania elementów członkowskich klasy, które nie powinny zostać utrwalone.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Aby zapobiec serializowana członka  
  
-   Zmień deklarację dla `PropertyChanged` zdarzeń w następujący sposób:  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 Następnym krokiem jest dodawanie do aplikacji LoanApp kodu serializacji. Aby można było serializować klasy i zapisze go w pliku, którego użyjesz <xref:System.IO> i <xref:System.Xml.Serialization> przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do bibliotek niezbędne klasy.  
  
### <a name="to-add-references-to-namespaces"></a>Aby dodać odwołania do przestrzeni nazw  
  
-   Dodaj następujące instrukcje na początku `Form1` klasy:  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     W tym przypadku są przy użyciu binarnej elementu formatującego do zapisania obiektu w formacie binarnym.  
  
 Następnym krokiem jest Dodaj kod, aby deserializować obiektu z pliku po utworzeniu obiektu.  
  
### <a name="to-deserialize-an-object"></a>Do deserializacji obiektu  
  
1.  Dodaj stałą do klasy dla nazwy pliku danych serializacji.  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  Zmodyfikuj kod `Form1_Load` procedury zdarzenia w następujący sposób:  
  
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
  
     Należy pamiętać, że musisz najpierw sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy odczytanie pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku. Należy również konwertować z typu stream z typem obiektu pożyczki.  
  
 Następnie należy dodać kod, aby zapisać dane wprowadzane w polach tekstowych do `Loan` klasy, a następnie musi serializować klasy w pliku.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Zapisz dane i serializować klasy  
  
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
  
 W tym momencie możesz ponownie skompilować i uruchomić aplikację. Początkowo wartości domyślne są wyświetlane w polach tekstowych. Spróbuj zmienić wartości i wprowadź nazwę w polu tekstowym czwarty. Zamknij aplikację i uruchom go ponownie. Należy pamiętać, że pojawią się nowe wartości w polach tekstowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja (Visual Basic)](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [Przewodnik programowania w języku Visual Basic](../../../../visual-basic/programming-guide/index.md)
