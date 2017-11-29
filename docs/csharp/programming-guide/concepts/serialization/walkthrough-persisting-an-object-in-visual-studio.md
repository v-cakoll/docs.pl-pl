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
ms.openlocfilehash: efdf4694c1a1b6df2e9531a2bb4c813b536a330e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-c"></a><span data-ttu-id="d2889-102">Wskazówki: Przechowywanie obiektu w programie Visual Studio (C#)</span><span class="sxs-lookup"><span data-stu-id="d2889-102">Walkthrough: Persisting an Object in Visual Studio (C#)</span></span>
<span data-ttu-id="d2889-103">Mimo że można ustawić właściwości obiektu do wartości domyślnych w czasie projektowania, wartości wprowadzone w czasie wykonywania zostaną utracone, gdy obiekt zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="d2889-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="d2889-104">Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, które umożliwia przechowywanie wartości i pobrać je przy następnym uruchomieniu tworzenia wystąpienia obiektu klasy.</span><span class="sxs-lookup"><span data-stu-id="d2889-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
 <span data-ttu-id="d2889-105">W tym przewodniku, utworzysz prostą `Loan` obiekt i utrwala jego danych do pliku.</span><span class="sxs-lookup"><span data-stu-id="d2889-105">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="d2889-106">Następnie zostanie pobrać dane z pliku podczas ponownego tworzenia obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2889-106">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2889-107">W tym przykładzie tworzy nowy plik, jeśli plik już nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="d2889-107">This example creates a new file if the file does not already exist.</span></span> <span data-ttu-id="d2889-108">Jeśli aplikacja musi utworzyć plik, ta aplikacja musi `Create` uprawnienia do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="d2889-108">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="d2889-109">Uprawnienia są skonfigurowane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="d2889-109">Permissions are set by using access control lists.</span></span> <span data-ttu-id="d2889-110">Jeśli plik już istnieje, aplikacja musi tylko `Write` uprawnienia, mniejszym uprawnień.</span><span class="sxs-lookup"><span data-stu-id="d2889-110">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="d2889-111">Jeśli to możliwe, jest bardziej bezpieczne tworzenie pliku podczas wdrażania i udzielać tylko `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu).</span><span class="sxs-lookup"><span data-stu-id="d2889-111">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="d2889-112">Ponadto jest bardziej bezpieczne można zapisać danych do folderów użytkownika niż w folderze głównym lub folderze Program Files.</span><span class="sxs-lookup"><span data-stu-id="d2889-112">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="d2889-113">W tym przykładzie przechowuje dane w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="d2889-113">This example stores data in a binary format file.</span></span> <span data-ttu-id="d2889-114">Nie można używać tych formatów dla poufnych danych, takie jak hasła lub karty kredytowej.</span><span class="sxs-lookup"><span data-stu-id="d2889-114">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d2889-115">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="d2889-115">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="d2889-116">Aby zmienić ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="d2889-116">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="d2889-117">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="d2889-117">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="d2889-118">Tworzenie obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="d2889-118">Creating the Loan Object</span></span>  
 <span data-ttu-id="d2889-119">Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja testowa, który używa klasy.</span><span class="sxs-lookup"><span data-stu-id="d2889-119">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="d2889-120">Aby utworzyć klasę pożyczki</span><span class="sxs-lookup"><span data-stu-id="d2889-120">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="d2889-121">Tworzenie nowego projektu biblioteki klas i nadaj jej nazwę na "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="d2889-121">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="d2889-122">Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="d2889-122">For more information, see [Creating Solutions and Projects](/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="d2889-123">W **Eksploratora rozwiązań**, otwórz plik Class1 menu skrótów i wybierz polecenie **zmienić**.</span><span class="sxs-lookup"><span data-stu-id="d2889-123">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="d2889-124">Zmień nazwę pliku do `Loan` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="d2889-124">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="d2889-125">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `Loan`.</span><span class="sxs-lookup"><span data-stu-id="d2889-125">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="d2889-126">Dodaj następujące publiczne elementy członkowskie do klasy:</span><span class="sxs-lookup"><span data-stu-id="d2889-126">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="d2889-127">Należy także utworzyć prostą aplikację, która używa `Loan` klasy.</span><span class="sxs-lookup"><span data-stu-id="d2889-127">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="d2889-128">Aby utworzyć aplikację testu</span><span class="sxs-lookup"><span data-stu-id="d2889-128">To create a test application</span></span>  
  
1.  <span data-ttu-id="d2889-129">Aby dodać projekt aplikacji formularzy systemu Windows do rozwiązania, na **pliku** menu, wybierz **Dodaj**, **nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="d2889-129">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**, **New Project**.</span></span>  
  
2.  <span data-ttu-id="d2889-130">W **Dodawanie nowego projektu** oknie dialogowym wybierz **aplikacji Windows Forms**i wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe .</span><span class="sxs-lookup"><span data-stu-id="d2889-130">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="d2889-131">W **Eksploratora rozwiązań**, wybierz projekt LoanApp.</span><span class="sxs-lookup"><span data-stu-id="d2889-131">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="d2889-132">Na **projektu** menu, wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="d2889-132">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="d2889-133">Na **projektu** menu, wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="d2889-133">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="d2889-134">W **Dodaj odwołanie** oknie dialogowym wybierz **projekty** karcie, a następnie wybierz projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="d2889-134">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="d2889-135">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="d2889-135">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="d2889-136">W projektancie, dodaj cztery <xref:System.Windows.Forms.TextBox> formantów w formularzu.</span><span class="sxs-lookup"><span data-stu-id="d2889-136">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="d2889-137">W Edytorze kodu dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="d2889-137">In the Code Editor, add the following code:</span></span>  
  
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
  
10. <span data-ttu-id="d2889-138">Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzeń do formularza przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="d2889-138">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```csharp  
    private void CustomerPropertyChanged(object sender,   
        System.ComponentModel.PropertyChangedEventArgs e)  
    {  
        MessageBox.Show(e.PropertyName + " has been changed.");  
    }  
    ```  
  
 <span data-ttu-id="d2889-139">W tym momencie możesz skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d2889-139">At this point, you can build and run the application.</span></span> <span data-ttu-id="d2889-140">Należy pamiętać, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="d2889-140">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="d2889-141">Zmień wartość stopy z 7.5 7.1, a następnie zamknij aplikację i uruchom go ponownie spróbuj — przywraca wartość domyślną w wersji 7.5.</span><span class="sxs-lookup"><span data-stu-id="d2889-141">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="d2889-142">W świecie rzeczywistym odsetek zmienić okresowo, ale niekoniecznie każdym uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2889-142">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="d2889-143">Zamiast wprowadzania użytkownika zaktualizować stopie procentowej zawsze jest uruchomiona aplikacja, zaleca się zachowanie najnowszych stopie procentowej między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d2889-143">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="d2889-144">W następnym kroku zostanie czy właśnie tę dodając serializacji do klasy pożyczki.</span><span class="sxs-lookup"><span data-stu-id="d2889-144">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="d2889-145">Za pomocą serializacji, aby utrwalić obiektu</span><span class="sxs-lookup"><span data-stu-id="d2889-145">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="d2889-146">Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę atrybutem `Serializable` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d2889-146">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="d2889-147">Aby oznaczyć klasę jako możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="d2889-147">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="d2889-148">Zmień deklaracji klasy dla klasy pożyczki w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d2889-148">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```csharp  
    [Serializable()]  
    public class Loan : System.ComponentModel.INotifyPropertyChanged  
    {  
    ```  
  
 <span data-ttu-id="d2889-149">`Serializable` Atrybut informuje kompilator, że wszystkie elementy w klasie mógł być trwały do pliku.</span><span class="sxs-lookup"><span data-stu-id="d2889-149">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="d2889-150">Ponieważ `PropertyChanged` zdarzenie jest obsługiwane przez obiekt formularza systemu Windows, nie można serializować.</span><span class="sxs-lookup"><span data-stu-id="d2889-150">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="d2889-151">`NonSerialized` Atrybut może służyć do oznaczania elementów członkowskich klasy, które nie powinny zostać utrwalone.</span><span class="sxs-lookup"><span data-stu-id="d2889-151">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="d2889-152">Aby zapobiec serializowana członka</span><span class="sxs-lookup"><span data-stu-id="d2889-152">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="d2889-153">Zmień deklarację dla `PropertyChanged` zdarzeń w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d2889-153">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```csharp  
    [field: NonSerialized()]  
    public event System.ComponentModel.PropertyChangedEventHandler PropertyChanged;  
    ```  
  
 <span data-ttu-id="d2889-154">Następnym krokiem jest dodawanie do aplikacji LoanApp kodu serializacji.</span><span class="sxs-lookup"><span data-stu-id="d2889-154">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="d2889-155">Aby można było serializować klasy i zapisze go w pliku, którego użyjesz <xref:System.IO> i <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="d2889-155">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="d2889-156">Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do bibliotek niezbędne klasy.</span><span class="sxs-lookup"><span data-stu-id="d2889-156">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="d2889-157">Aby dodać odwołania do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="d2889-157">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="d2889-158">Dodaj następujące instrukcje na początku `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="d2889-158">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```csharp  
    using System.IO;  
    using System.Runtime.Serialization.Formatters.Binary;  
    ```  
  
     <span data-ttu-id="d2889-159">W tym przypadku są przy użyciu binarnej elementu formatującego do zapisania obiektu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="d2889-159">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="d2889-160">Następnym krokiem jest Dodaj kod, aby deserializować obiektu z pliku po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="d2889-160">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="d2889-161">Do deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="d2889-161">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="d2889-162">Dodaj stałą do klasy dla nazwy pliku danych serializacji.</span><span class="sxs-lookup"><span data-stu-id="d2889-162">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```csharp  
    const string FileName = @"..\..\SavedLoan.bin";  
    ```  
  
2.  <span data-ttu-id="d2889-163">Zmodyfikuj kod `Form1_Load` procedury zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="d2889-163">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="d2889-164">Należy pamiętać, że musisz najpierw sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="d2889-164">Note that you first must check that the file exists.</span></span> <span data-ttu-id="d2889-165">Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy odczytanie pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku.</span><span class="sxs-lookup"><span data-stu-id="d2889-165">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="d2889-166">Należy również konwertować z typu stream z typem obiektu pożyczki.</span><span class="sxs-lookup"><span data-stu-id="d2889-166">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="d2889-167">Następnie należy dodać kod, aby zapisać dane wprowadzane w polach tekstowych do `Loan` klasy, a następnie musi serializować klasy w pliku.</span><span class="sxs-lookup"><span data-stu-id="d2889-167">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="d2889-168">Zapisz dane i serializować klasy</span><span class="sxs-lookup"><span data-stu-id="d2889-168">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="d2889-169">Dodaj następujący kod do `Form1_FormClosing` procedury zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="d2889-169">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="d2889-170">W tym momencie możesz ponownie skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="d2889-170">At this point, you can again build and run the application.</span></span> <span data-ttu-id="d2889-171">Początkowo wartości domyślne są wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="d2889-171">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="d2889-172">Spróbuj zmienić wartości i wprowadź nazwę w polu tekstowym czwarty.</span><span class="sxs-lookup"><span data-stu-id="d2889-172">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="d2889-173">Zamknij aplikację i uruchom go ponownie.</span><span class="sxs-lookup"><span data-stu-id="d2889-173">Close the application and then run it again.</span></span> <span data-ttu-id="d2889-174">Należy pamiętać, że pojawią się nowe wartości w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="d2889-174">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d2889-175">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d2889-175">See Also</span></span>  
 [<span data-ttu-id="d2889-176">Serializacja (C#)</span><span class="sxs-lookup"><span data-stu-id="d2889-176">Serialization (C# )</span></span>](../../../../csharp/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="d2889-177">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d2889-177">C# Programming Guide</span></span>](../../../../csharp/programming-guide/index.md)
