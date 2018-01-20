---
title: "Wskazówki: Przechowywanie obiektu w programie Visual Studio (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: get-started-article
ms.assetid: a544ce46-ee25-49da-afd4-457a3d59bf63
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b1a3fc377875ee25baa0718a25b5ac509822154
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a>Wskazówki: Przechowywanie obiektu w programie Visual Studio (C#)
Mimo że można ustawić właściwości obiektu do wartości domyślnych w czasie projektowania, wartości wprowadzone w czasie wykonywania zostaną utracone, gdy obiekt zostanie zniszczony. Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, które umożliwia przechowywanie wartości i pobrać je przy następnym uruchomieniu tworzenia wystąpienia obiektu klasy.  
  
 W tym przewodniku, utworzysz prostą `Loan` obiekt i utrwala jego danych do pliku. Następnie zostanie pobrać dane z pliku podczas ponownego tworzenia obiektu.  
  
> [!IMPORTANT]
>  W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje. Jeśli aplikacja musi utworzyć plik, ta aplikacja musi `Create` uprawnienia do tego folderu. Uprawnienia są skonfigurowane przy użyciu list kontroli dostępu. Jeśli plik już istnieje, aplikacja musi tylko `Write` uprawnienia, mniejszym uprawnień. Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu). Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.  
  
> [!IMPORTANT]
>  W tym przykładzie przechowuje dane w pliku binarnym. Nie można używać tych formatów dla poufnych danych, takie jak hasła lub karty kredytowej.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="creating-the-loan-object"></a>Tworzenie obiektu pożyczki  
 Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja testowa, który używa klasy.  
  
### <a name="to-create-the-loan-class"></a>Aby utworzyć klasę pożyczki  
  
1.  Tworzenie nowego projektu biblioteki klas i nadaj jej nazwę na "LoanClass". Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).  
  
2.  W **Eksploratora rozwiązań**, otwórz plik Class1 menu skrótów i wybierz polecenie **zmienić**. Zmień nazwę pliku do `Loan` i naciśnij klawisz ENTER. Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `Loan`.  
  
3.  Dodaj następujące publiczne elementy członkowskie do klasy:  
  
    ```csharp  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
        public double LoanAmount {get; set;}  
        public double InterestRate {get; set;}  
        public int Term {get; set;}  
  
        private string p_Customer;  
        public string Customer  
        {  
            get { return p_Customer; }  
            set   
            {  
                p_Customer = value;  
                PropertyChanged(this,  
                  new System.ComponentModel.PropertyChangedEventArgs("Customer"));  
            }  
        }  
  
        public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
  
        public Loan(double loanAmount,  
                    double interestRate,  
                    int term,  
                    string customer)  
        {  
            this.LoanAmount = loanAmount;  
            this.InterestRate = interestRate;  
            this.Term = term;  
            p_Customer = customer;  
        }  
    }  
    ```  
  
 Należy także utworzyć prostą aplikację, która używa `Loan` klasy.  
  
### <a name="to-create-a-test-application"></a>Aby utworzyć aplikację testu  
  
1.  Aby dodać projekt aplikacji formularzy systemu Windows do rozwiązania, na **pliku** menu, wybierz **Dodaj**, **nowy projekt**.  
  
2.  W **Dodawanie nowego projektu** oknie dialogowym wybierz **aplikacji Windows Forms**i wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe .  
  
3.  W **Eksploratora rozwiązań**, wybierz projekt LoanApp.  
  
4.  Na **projektu** menu, wybierz **Ustaw jako projekt startowy**.  
  
5.  Na **projektu** menu, wybierz **Dodaj odwołanie**.  
  
6.  W **Dodaj odwołanie** oknie dialogowym wybierz **projekty** karcie, a następnie wybierz projekt LoanClass.  
  
7.  Kliknij przycisk **OK** , aby zamknąć okno dialogowe.  
  
8.  W projektancie, dodaj cztery <xref:System.Windows.Forms.TextBox> formantów w formularzu.  
  
9. W Edytorze kodu dodaj następujący kod:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
10. Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzeń do formularza przy użyciu następującego kodu:  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 W tym momencie możesz skompilować i uruchomić aplikację. Należy pamiętać, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych. Zmień wartość stopy z 7.5 7.1, a następnie zamknij aplikację i uruchom go ponownie spróbuj — przywraca wartość domyślną w wersji 7.5.  
  
 W świecie rzeczywistym odsetek zmienić okresowo, ale niekoniecznie każdym uruchomieniu aplikacji. Zamiast wprowadzania użytkownika zaktualizować stopie procentowej zawsze jest uruchomiona aplikacja, zaleca się zachowanie najnowszych stopie procentowej między wystąpieniami aplikacji. W następnym kroku zostanie czy właśnie tę dodając serializacji do klasy pożyczki.  
  
## <a name="using-serialization-to-persist-the-object"></a>Za pomocą serializacji, aby utrwalić obiektu  
 Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę atrybutem `Serializable` atrybutu.  
  
### <a name="to-mark-a-class-as-serializable"></a>Aby oznaczyć klasę jako możliwy do serializacji  
  
-   Zmień deklaracji klasy dla klasy pożyczki w następujący sposób:  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 `Serializable` Atrybut informuje kompilator, że wszystkie elementy w klasie mógł być trwały do pliku. Ponieważ `PropertyChanged` zdarzenie jest obsługiwane przez obiekt formularza systemu Windows, nie można serializować. `NonSerialized` Atrybut może służyć do oznaczania elementów członkowskich klasy, które nie powinny zostać utrwalone.  
  
### <a name="to-prevent-a-member-from-being-serialized"></a>Aby zapobiec serializowana członka  
  
-   Zmień deklarację dla `PropertyChanged` zdarzeń w następujący sposób:  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 Następnym krokiem jest dodawanie do aplikacji LoanApp kodu serializacji. Aby można było serializować klasy i zapisze go w pliku, którego użyjesz <xref:System.IO> i <xref:System.Xml.Serialization> przestrzeni nazw. Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do bibliotek niezbędne klasy.  
  
### <a name="to-add-references-to-namespaces"></a>Aby dodać odwołania do przestrzeni nazw  
  
-   Dodaj następujące instrukcje na początku `Form1` klasy:  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     W tym przypadku są przy użyciu binarnej elementu formatującego do zapisania obiektu w formacie binarnym.  
  
 Następnym krokiem jest Dodaj kod, aby deserializować obiektu z pliku po utworzeniu obiektu.  
  
### <a name="to-deserialize-an-object"></a>Do deserializacji obiektu  
  
1.  Dodaj stałą do klasy dla nazwy pliku danych serializacji.  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  Zmodyfikuj kod `Form1_Load` procedury zdarzenia w następujący sposób:  
  
    ```csharp  
    private LoanClass.Loan TestLoan = new LoanClass.Loan(10000.0, 0.075, 36, "Neil Black");  
  
    private void Form1_Load(object sender, EventArgs e)  
    {  
        if (File.Exists(FileName))  
        {  
            Stream TestFileStream = File.OpenRead(FileName);  
            BinaryFormatter deserializer = new BinaryFormatter();  
            TestLoan = (LoanClass.Loan)deserializer.Deserialize(TestFileStream);  
            TestFileStream.Close();  
        }  
  
        TestLoan.PropertyChanged += this.CustomerPropertyChanged;  
  
        textBox1.Text = TestLoan.LoanAmount.ToString();  
        textBox2.Text = TestLoan.InterestRate.ToString();  
        textBox3.Text = TestLoan.Term.ToString();  
        textBox4.Text = TestLoan.Customer;  
    }  
    ```  
  
     Należy pamiętać, że musisz najpierw sprawdzić, czy plik istnieje. Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy odczytanie pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku. Należy również konwertować z typu stream z typem obiektu pożyczki.  
  
 Następnie należy dodać kod, aby zapisać dane wprowadzane w polach tekstowych do `Loan` klasy, a następnie musi serializować klasy w pliku.  
  
### <a name="to-save-the-data-and-serialize-the-class"></a>Zapisz dane i serializować klasy  
  
-   Dodaj następujący kod do `Form1_FormClosing` procedury zdarzenia:  
  
    ```csharp  
    private void Form1_FormClosing(object sender, FormClosingEventArgs e)  
    {  
        TestLoan.LoanAmount = Convert.ToDouble(textBox1.Text);  
        TestLoan.InterestRate = Convert.ToDouble(textBox2.Text);  
        TestLoan.Term = Convert.ToInt32(textBox3.Text);  
        TestLoan.Customer = textBox4.Text;  
  
        Stream TestFileStream = File.Create(FileName);  
        BinaryFormatter serializer = new BinaryFormatter();  
        serializer.Serialize(TestFileStream, TestLoan);  
        TestFileStream.Close();  
    }  
    ```  
  
 W tym momencie możesz ponownie skompilować i uruchomić aplikację. Początkowo wartości domyślne są wyświetlane w polach tekstowych. Spróbuj zmienić wartości i wprowadź nazwę w polu tekstowym czwarty. Zamknij aplikację i uruchom go ponownie. Należy pamiętać, że pojawią się nowe wartości w polach tekstowych.  
  
## <a name="see-also"></a>Zobacz też  
 [Serializacja (C#)](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [Przewodnik programowania w języku C#](../../../../csharp/programming-guide/index.md)
