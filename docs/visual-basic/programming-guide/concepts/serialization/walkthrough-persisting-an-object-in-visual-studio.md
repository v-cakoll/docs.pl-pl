---
title: Przechowywanie obiektu w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 25951327028b9b8ced8506b3ba6395e8c9e6abed
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43483687"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="3279d-102">Przewodnik: Przechowywanie obiektu w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3279d-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="3279d-103">Chociaż można ustawić właściwości obiektu do wartości domyślnych w czasie projektowania, wszystkie wartości wprowadzone w czasie wykonywania zostaną utracone, kiedy niszczony jest obiekt.</span><span class="sxs-lookup"><span data-stu-id="3279d-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="3279d-104">Można użyć serializacji do utrwalenia danych obiektu między wystąpieniami, dzięki czemu możesz przechowywać wartości, a następnie pobrać jednego z nich przy następnym uruchomieniu jest tworzone wystąpienie obiektu.</span><span class="sxs-lookup"><span data-stu-id="3279d-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3279d-105">W Visual Basic do przechowywania danych proste, takie jak nazwa lub numer, można użyć `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="3279d-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="3279d-106">Aby uzyskać więcej informacji, zobacz [My.Settings — obiekt](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="3279d-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="3279d-107">W tym instruktażu utworzysz prostą `Loan` obiekt i utrwala jego dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="3279d-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="3279d-108">Następnie powoduje pobranie danych z pliku, gdy ponownie utworzyć obiekt.</span><span class="sxs-lookup"><span data-stu-id="3279d-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3279d-109">W tym przykładzie tworzy nowy plik, jeśli go jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="3279d-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="3279d-110">Jeśli aplikacja musi utworzyć plik, ta aplikacja musi `Create` uprawnienie do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="3279d-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="3279d-111">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="3279d-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="3279d-112">Jeśli plik już istnieje, aplikacja potrzebuje tylko `Write` uprawnienia, mniejsze uprawnienia.</span><span class="sxs-lookup"><span data-stu-id="3279d-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="3279d-113">Jeśli to możliwe, bezpieczniej jest tworzyć plik podczas wdrożenia i udzielić `Read` uprawnienia do pojedynczego pliku (zamiast tworzenia uprawnień dla folderu).</span><span class="sxs-lookup"><span data-stu-id="3279d-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="3279d-114">Ponadto jest bardziej bezpieczne, można zapisać danych do folderów użytkowników niż do folderu głównego lub do folderu Program Files.</span><span class="sxs-lookup"><span data-stu-id="3279d-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="3279d-115">W tym przykładzie przechowuje dane w pliku binarnym.</span><span class="sxs-lookup"><span data-stu-id="3279d-115">This example stores data in a binary.</span></span> <span data-ttu-id="3279d-116">Nie można używać tych formatów poufnych danych, takie jak hasła lub informacji o karcie kredytowej.</span><span class="sxs-lookup"><span data-stu-id="3279d-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3279d-117">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="3279d-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="3279d-118">Aby zmienić swoje ustawienia, kliknij przycisk **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="3279d-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="3279d-119">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="3279d-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="3279d-120">Tworzenie obiektu pożyczki</span><span class="sxs-lookup"><span data-stu-id="3279d-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="3279d-121">Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacja testowa, która używa klasy.</span><span class="sxs-lookup"><span data-stu-id="3279d-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="3279d-122">Aby utworzyć klasę pożyczki</span><span class="sxs-lookup"><span data-stu-id="3279d-122">To create the Loan class</span></span>  
  
1.  <span data-ttu-id="3279d-123">Utwórz nowy projekt biblioteki klas i nadaj mu nazwę "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="3279d-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="3279d-124">Aby uzyskać więcej informacji, zobacz [tworzenie rozwiązań i projektów](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="3279d-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2.  <span data-ttu-id="3279d-125">W **Eksploratora rozwiązań**, otwórz menu skrótów dla pliku Class1 i wybierz **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="3279d-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="3279d-126">Zmień nazwę pliku do `Loan` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="3279d-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="3279d-127">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy, która ma `Loan`.</span><span class="sxs-lookup"><span data-stu-id="3279d-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3.  <span data-ttu-id="3279d-128">Dodaj następujące składowe publiczne klasy:</span><span class="sxs-lookup"><span data-stu-id="3279d-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="3279d-129">Ponadto trzeba będzie utworzyć prostą aplikację, która używa `Loan` klasy.</span><span class="sxs-lookup"><span data-stu-id="3279d-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="3279d-130">Aby utworzyć aplikację testu</span><span class="sxs-lookup"><span data-stu-id="3279d-130">To create a test application</span></span>  
  
1.  <span data-ttu-id="3279d-131">Aby dodać projekt aplikacja interfejsu Windows Forms do rozwiązania, na **pliku** menu, wybierz **Dodaj**,**nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="3279d-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2.  <span data-ttu-id="3279d-132">W **Dodaj nowy projekt** okna dialogowego wybierz **aplikacja interfejsu Windows Forms**, a następnie wprowadź `LoanApp` jako nazwę projektu, a następnie kliknij przycisk **OK** aby zamknąć okno dialogowe .</span><span class="sxs-lookup"><span data-stu-id="3279d-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3.  <span data-ttu-id="3279d-133">W **Eksploratora rozwiązań**, wybierz projekt LoanApp.</span><span class="sxs-lookup"><span data-stu-id="3279d-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4.  <span data-ttu-id="3279d-134">Na **projektu** menu, wybierz **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="3279d-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5.  <span data-ttu-id="3279d-135">Na **projektu** menu, wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="3279d-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6.  <span data-ttu-id="3279d-136">W **Dodaj odwołanie** okna dialogowego wybierz **projektów** kartę, a następnie wybierz projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="3279d-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7.  <span data-ttu-id="3279d-137">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="3279d-137">Click **OK** to close the dialog box.</span></span>  
  
8.  <span data-ttu-id="3279d-138">W projektancie, dodaj cztery <xref:System.Windows.Forms.TextBox> formantów do formularza.</span><span class="sxs-lookup"><span data-stu-id="3279d-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="3279d-139">W Edytorze kodu dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="3279d-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="3279d-140">Dodawanie obsługi zdarzeń dla `PropertyChanged` zdarzeń do formularza przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="3279d-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="3279d-141">W tym momencie można tworzyć i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="3279d-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="3279d-142">Należy zauważyć, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3279d-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="3279d-143">Spróbuj zmienić wartość stopy z 7,5 na 7.1, zamknij aplikację i ponownie uruchom — przywraca wartość domyślną w wersji 7.5.</span><span class="sxs-lookup"><span data-stu-id="3279d-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="3279d-144">W świecie rzeczywistym oprocentowania zmienić okresowo, ale niekoniecznie każdorazowym uruchomieniu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3279d-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="3279d-145">Zamiast wprowadzania użytkownika zaktualizować stopę każdorazowym uruchomieniu aplikacji, lepiej jest zapewnienie najnowszych stopie między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="3279d-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="3279d-146">W następnym kroku będziesz robić to dodając serializacji do klasy pożyczki.</span><span class="sxs-lookup"><span data-stu-id="3279d-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="3279d-147">Za pomocą serializacji, aby utrwalić obiektu</span><span class="sxs-lookup"><span data-stu-id="3279d-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="3279d-148">Aby zachować wartości dla klasy pożyczki, należy oznaczyć klasę za pomocą `Serializable` atrybutu.</span><span class="sxs-lookup"><span data-stu-id="3279d-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="3279d-149">Aby oznaczyć klasę jako możliwe do serializacji</span><span class="sxs-lookup"><span data-stu-id="3279d-149">To mark a class as serializable</span></span>  
  
-   <span data-ttu-id="3279d-150">Zmień deklarację klasy dla klasy pożyczek w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3279d-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="3279d-151">`Serializable` Atrybut informuje kompilator, że wszystkie elementy w klasie mogą zostać utrwalone w pliku.</span><span class="sxs-lookup"><span data-stu-id="3279d-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="3279d-152">Ponieważ `PropertyChanged` zdarzenie jest obsługiwane przez obiekt formularza Windows, nie może być serializowany.</span><span class="sxs-lookup"><span data-stu-id="3279d-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="3279d-153">`NonSerialized` Atrybut może służyć do oznaczania składowych klasy, które nie powinny zostać utrwalone.</span><span class="sxs-lookup"><span data-stu-id="3279d-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="3279d-154">Aby zapobiec elementu członkowskiego serializowanego</span><span class="sxs-lookup"><span data-stu-id="3279d-154">To prevent a member from being serialized</span></span>  
  
-   <span data-ttu-id="3279d-155">Zmienianie deklaracji pod kątem `PropertyChanged` zdarzeń w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3279d-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="3279d-156">Następnym krokiem jest dodać kod serializacji do aplikacji LoanApp.</span><span class="sxs-lookup"><span data-stu-id="3279d-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="3279d-157">Aby można było serializować klasy i zapisze go w pliku, użyjesz <xref:System.IO> i <xref:System.Xml.Serialization> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="3279d-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="3279d-158">Aby uniknąć wpisywania w pełni kwalifikowane nazwy, można dodać odwołania do bibliotek klas niezbędne.</span><span class="sxs-lookup"><span data-stu-id="3279d-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="3279d-159">Aby dodać odwołania do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="3279d-159">To add references to namespaces</span></span>  
  
-   <span data-ttu-id="3279d-160">Dodaj następujące instrukcje na górze `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="3279d-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="3279d-161">W tym przypadku używasz binarny program formatujący pozwala zapisać obiekt w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="3279d-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="3279d-162">Następnym krokiem jest dodawanie kodu do deserializacji obiektu na podstawie pliku, gdy obiekt zostanie utworzony.</span><span class="sxs-lookup"><span data-stu-id="3279d-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="3279d-163">Do deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="3279d-163">To deserialize an object</span></span>  
  
1.  <span data-ttu-id="3279d-164">Dodaj stałą do klasy dla nazwy pliku serializowane dane.</span><span class="sxs-lookup"><span data-stu-id="3279d-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2.  <span data-ttu-id="3279d-165">Zmodyfikuj kod `Form1_Load` procedury zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="3279d-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="3279d-166">Pamiętaj, że najpierw należy sprawdzić czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="3279d-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="3279d-167">Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasy można odczytać pliku binarnego i <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> klasy do tłumaczenia pliku.</span><span class="sxs-lookup"><span data-stu-id="3279d-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="3279d-168">Należy również konwersji z typu strumienia do typu obiektu pożyczki.</span><span class="sxs-lookup"><span data-stu-id="3279d-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="3279d-169">Następnie należy dodać kod, aby zapisać dane wprowadzone w polach tekstowych do `Loan` klasy, a następnie muszą serializację klasy w pliku.</span><span class="sxs-lookup"><span data-stu-id="3279d-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="3279d-170">Aby zapisać dane i serializacji klasę</span><span class="sxs-lookup"><span data-stu-id="3279d-170">To save the data and serialize the class</span></span>  
  
-   <span data-ttu-id="3279d-171">Dodaj następujący kod do `Form1_FormClosing` procedury zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="3279d-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="3279d-172">W tym momencie możesz ponownie skompiluj i uruchom aplikację.</span><span class="sxs-lookup"><span data-stu-id="3279d-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="3279d-173">Początkowo wartości domyślne są wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3279d-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="3279d-174">Spróbuj zmienić wartości i wprowadź nazwę w polu tekstowym czwarty.</span><span class="sxs-lookup"><span data-stu-id="3279d-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="3279d-175">Zamknij aplikację, a następnie uruchom ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="3279d-175">Close the application and then run it again.</span></span> <span data-ttu-id="3279d-176">Pamiętaj, że pojawiają się nowe wartości w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="3279d-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3279d-177">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3279d-177">See Also</span></span>  
 [<span data-ttu-id="3279d-178">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3279d-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)  
 [<span data-ttu-id="3279d-179">Przewodnik programowania w języku Visual Basic</span><span class="sxs-lookup"><span data-stu-id="3279d-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
