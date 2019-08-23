---
title: Utrwalanie obiektu w programie Visual Studio (Visual Basic)
ms.date: 07/20/2015
ms.assetid: f1d0b562-e349-4dce-ab5f-c05108467030
ms.openlocfilehash: 6f25c2a6f06b56dcbb5ba7e63165d06ff77d9ca8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69937360"
---
# <a name="walkthrough-persisting-an-object-in-visual-studio-visual-basic"></a><span data-ttu-id="1e36a-102">Przewodnik: Utrwalanie obiektu w programie Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e36a-102">Walkthrough: Persisting an Object in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="1e36a-103">Chociaż właściwości obiektu można ustawić na wartości domyślne w czasie projektowania, wszelkie wartości wprowadzone w czasie wykonywania są tracone, gdy obiekt zostanie zniszczony.</span><span class="sxs-lookup"><span data-stu-id="1e36a-103">Although you can set an object's properties to default values at design time, any values entered at run time are lost when the object is destroyed.</span></span> <span data-ttu-id="1e36a-104">Możesz użyć serializacji, aby zachować dane obiektu między wystąpieniami, co umożliwia przechowywanie wartości i pobieranie ich przy następnym utworzeniu wystąpienia obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-104">You can use serialization to persist an object's data between instances, which enables you to store values and retrieve them the next time that the object is instantiated.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e36a-105">W Visual Basic, aby przechowywać proste dane, takie jak nazwa lub liczba, można użyć `My.Settings` obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-105">In Visual Basic, to store simple data, such as a name or number, you can use the `My.Settings` object.</span></span> <span data-ttu-id="1e36a-106">Aby uzyskać więcej informacji, zobacz [My. Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span><span class="sxs-lookup"><span data-stu-id="1e36a-106">For more information, see [My.Settings Object](../../../../visual-basic/language-reference/objects/my-settings-object.md).</span></span>  
  
 <span data-ttu-id="1e36a-107">W tym instruktażu utworzysz prosty `Loan` obiekt i zachowasz jego dane do pliku.</span><span class="sxs-lookup"><span data-stu-id="1e36a-107">In this walkthrough, you will create a simple `Loan` object and persist its data to a file.</span></span> <span data-ttu-id="1e36a-108">Następnie dane zostaną pobrane z pliku po ponownym utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-108">You will then retrieve the data from the file when you re-create the object.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e36a-109">Ten przykład tworzy nowy plik, jeśli plik jeszcze nie istnieje.</span><span class="sxs-lookup"><span data-stu-id="1e36a-109">This example creates a new file, if the file does not already exist.</span></span> <span data-ttu-id="1e36a-110">Jeśli aplikacja musi utworzyć plik, aplikacja musi mieć `Create` uprawnienia do tego folderu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-110">If an application must create a file, that application must `Create` permission for the folder.</span></span> <span data-ttu-id="1e36a-111">Uprawnienia są ustawiane przy użyciu list kontroli dostępu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-111">Permissions are set by using access control lists.</span></span> <span data-ttu-id="1e36a-112">Jeśli plik już istnieje, aplikacja wymaga tylko `Write` uprawnień, ale jest to małe uprawnienie.</span><span class="sxs-lookup"><span data-stu-id="1e36a-112">If the file already exists, the application needs only `Write` permission, a lesser permission.</span></span> <span data-ttu-id="1e36a-113">Jeśli to możliwe, bezpieczniejsze jest tworzenie plików podczas wdrażania i udzielanie `Read` uprawnień tylko jednemu plikowi (zamiast tworzenia uprawnień dla folderu).</span><span class="sxs-lookup"><span data-stu-id="1e36a-113">Where possible, it is more secure to create the file during deployment, and only grant `Read` permissions to a single file (instead of Create permissions for a folder).</span></span> <span data-ttu-id="1e36a-114">Ponadto bardziej bezpieczne jest zapisanie danych do folderów użytkowników niż folder główny lub folder Program Files.</span><span class="sxs-lookup"><span data-stu-id="1e36a-114">Also, it is more secure to write data to user folders than to the root folder or the Program Files folder.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="1e36a-115">Ten przykład zapisuje dane w postaci binarnej.</span><span class="sxs-lookup"><span data-stu-id="1e36a-115">This example stores data in a binary.</span></span> <span data-ttu-id="1e36a-116">Tych formatów nie należy używać w przypadku poufnych danych, takich jak hasła lub informacje o kartach kredytowych.</span><span class="sxs-lookup"><span data-stu-id="1e36a-116">These formats should not be used for sensitive data, such as passwords or credit-card information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1e36a-117">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="1e36a-117">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="1e36a-118">Aby zmienić ustawienia, kliknij przycisk **Importuj i Eksportuj ustawienia** w menu **Narzędzia** .</span><span class="sxs-lookup"><span data-stu-id="1e36a-118">To change your settings, click **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="1e36a-119">Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="1e36a-119">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
## <a name="creating-the-loan-object"></a><span data-ttu-id="1e36a-120">Tworzenie obiektu pożyczek</span><span class="sxs-lookup"><span data-stu-id="1e36a-120">Creating the Loan Object</span></span>  
 <span data-ttu-id="1e36a-121">Pierwszym krokiem jest utworzenie `Loan` klasy i aplikacji testowej, która używa klasy.</span><span class="sxs-lookup"><span data-stu-id="1e36a-121">The first step is to create a `Loan` class and a test application that uses the class.</span></span>  
  
### <a name="to-create-the-loan-class"></a><span data-ttu-id="1e36a-122">Aby utworzyć klasę pożyczek</span><span class="sxs-lookup"><span data-stu-id="1e36a-122">To create the Loan class</span></span>  
  
1. <span data-ttu-id="1e36a-123">Utwórz nowy projekt biblioteki klas i nadaj mu nazwę "LoanClass".</span><span class="sxs-lookup"><span data-stu-id="1e36a-123">Create a new Class Library project and name it "LoanClass".</span></span> <span data-ttu-id="1e36a-124">Aby uzyskać więcej informacji, zobacz [Tworzenie rozwiązań i projektów](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span><span class="sxs-lookup"><span data-stu-id="1e36a-124">For more information, see [Creating Solutions and Projects](https://docs.microsoft.com/visualstudio/ide/creating-solutions-and-projects).</span></span>  
  
2. <span data-ttu-id="1e36a-125">W **Eksplorator rozwiązań**Otwórz menu skrótów dla pliku Class1 i wybierz polecenie **Zmień nazwę**.</span><span class="sxs-lookup"><span data-stu-id="1e36a-125">In **Solution Explorer**, open the shortcut menu for the Class1 file and choose **Rename**.</span></span> <span data-ttu-id="1e36a-126">Zmień nazwę pliku na `Loan` i naciśnij klawisz ENTER.</span><span class="sxs-lookup"><span data-stu-id="1e36a-126">Rename the file to `Loan` and press ENTER.</span></span> <span data-ttu-id="1e36a-127">Zmiana nazwy pliku spowoduje również zmianę nazwy klasy na `Loan`.</span><span class="sxs-lookup"><span data-stu-id="1e36a-127">Renaming the file will also rename the class to `Loan`.</span></span>  
  
3. <span data-ttu-id="1e36a-128">Dodaj następujące publiczne elementy członkowskie do klasy:</span><span class="sxs-lookup"><span data-stu-id="1e36a-128">Add the following public members to the class:</span></span>  
  
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
  
 <span data-ttu-id="1e36a-129">Należy również utworzyć prostą aplikację, która używa `Loan` klasy.</span><span class="sxs-lookup"><span data-stu-id="1e36a-129">You will also have to create a simple application that uses the `Loan` class.</span></span>  
  
### <a name="to-create-a-test-application"></a><span data-ttu-id="1e36a-130">Aby utworzyć aplikację testową</span><span class="sxs-lookup"><span data-stu-id="1e36a-130">To create a test application</span></span>  
  
1. <span data-ttu-id="1e36a-131">Aby dodać projekt aplikacji Windows Forms do rozwiązania, w menu **plik** wybierz polecenie **Dodaj**,**Nowy projekt**.</span><span class="sxs-lookup"><span data-stu-id="1e36a-131">To add a Windows Forms Application project to your solution, on the **File** menu, choose **Add**,**New Project**.</span></span>  
  
2. <span data-ttu-id="1e36a-132">W oknie dialogowym **Dodaj nowy projekt** wybierz pozycję **Windows Forms aplikacja**i wprowadź `LoanApp` nazwę projektu, a następnie kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1e36a-132">In the **Add New Project** dialog box, choose **Windows Forms Application**, and enter `LoanApp` as the name of the project, and then click **OK** to close the dialog box.</span></span>  
  
3. <span data-ttu-id="1e36a-133">W **Eksplorator rozwiązań**wybierz projekt LoanApp.</span><span class="sxs-lookup"><span data-stu-id="1e36a-133">In **Solution Explorer**, choose the LoanApp project.</span></span>  
  
4. <span data-ttu-id="1e36a-134">W menu **projekt** wybierz pozycję **Ustaw jako projekt startowy**.</span><span class="sxs-lookup"><span data-stu-id="1e36a-134">On the **Project** menu, choose **Set as StartUp Project**.</span></span>  
  
5. <span data-ttu-id="1e36a-135">Na **projektu** menu, wybierz **Dodaj odwołanie**.</span><span class="sxs-lookup"><span data-stu-id="1e36a-135">On the **Project** menu, choose **Add Reference**.</span></span>  
  
6. <span data-ttu-id="1e36a-136">W oknie dialogowym **Dodaj odwołanie** wybierz kartę **projekty** , a następnie wybierz projekt LoanClass.</span><span class="sxs-lookup"><span data-stu-id="1e36a-136">In the **Add Reference** dialog box, choose the **Projects** tab and then choose the LoanClass project.</span></span>  
  
7. <span data-ttu-id="1e36a-137">Kliknij przycisk **OK** , aby zamknąć okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="1e36a-137">Click **OK** to close the dialog box.</span></span>  
  
8. <span data-ttu-id="1e36a-138">W projektancie Dodaj cztery <xref:System.Windows.Forms.TextBox> kontrolki do formularza.</span><span class="sxs-lookup"><span data-stu-id="1e36a-138">In the designer, add four <xref:System.Windows.Forms.TextBox> controls to the form.</span></span>  
  
9. <span data-ttu-id="1e36a-139">W Edytorze kodu dodaj następujący kod:</span><span class="sxs-lookup"><span data-stu-id="1e36a-139">In the Code Editor, add the following code:</span></span>  
  
    ```vb  
    Private WithEvents TestLoan As New LoanClass.Loan(10000.0, 0.075, 36, "Neil Black")  
  
    Private Sub Form1_Load() Handles MyBase.Load  
        TextBox1.Text = TestLoan.LoanAmount.ToString  
        TextBox2.Text = TestLoan.InterestRate.ToString  
        TextBox3.Text = TestLoan.Term.ToString  
        TextBox4.Text = TestLoan.Customer  
    End Sub  
    ```  
  
10. <span data-ttu-id="1e36a-140">Dodaj program obsługi zdarzeń dla `PropertyChanged` zdarzenia do formularza przy użyciu następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="1e36a-140">Add an event handler for the `PropertyChanged` event to the form by using the following code:</span></span>  
  
    ```vb  
    Public Sub CustomerPropertyChanged(  
          ByVal sender As Object,  
          ByVal e As System.ComponentModel.PropertyChangedEventArgs  
        ) Handles TestLoan.PropertyChanged  
  
        MsgBox(e.PropertyName & " has been changed.")  
    End Sub  
    ```  
  
 <span data-ttu-id="1e36a-141">W tym momencie można skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1e36a-141">At this point, you can build and run the application.</span></span> <span data-ttu-id="1e36a-142">Należy zauważyć, że wartości domyślne z `Loan` klasy są wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="1e36a-142">Note that the default values from the `Loan` class appear in the text boxes.</span></span> <span data-ttu-id="1e36a-143">Spróbuj zmienić wartość stopy oprocentowania z 7,5 na 7,1, a następnie zamknij aplikację i uruchom ją ponownie — wartość zostanie przywrócona do wartości domyślnej 7,5.</span><span class="sxs-lookup"><span data-stu-id="1e36a-143">Try to change the interest-rate value from 7.5 to 7.1, and then close the application and run it again—the value reverts to the default of 7.5.</span></span>  
  
 <span data-ttu-id="1e36a-144">W świecie rzeczywistym stawki odsetek zmieniają się okresowo, ale nie zawsze, gdy aplikacja jest uruchomiona.</span><span class="sxs-lookup"><span data-stu-id="1e36a-144">In the real world, interest rates change periodically, but not necessarily every time that the application is run.</span></span> <span data-ttu-id="1e36a-145">Zamiast sprawiać, że użytkownik nie aktualizuje stopy oprocentowania za każdym razem, gdy aplikacja jest uruchomiona, lepiej jest zachować najnowszą stawkę odsetek między wystąpieniami aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1e36a-145">Rather than making the user update the interest rate every time that the application runs, it is better to preserve the most recent interest rate between instances of the application.</span></span> <span data-ttu-id="1e36a-146">W następnym kroku wystarczy dodać serializację do klasy pożyczek.</span><span class="sxs-lookup"><span data-stu-id="1e36a-146">In the next step, you will do just that by adding serialization to the Loan class.</span></span>  
  
## <a name="using-serialization-to-persist-the-object"></a><span data-ttu-id="1e36a-147">Utrwalanie obiektu przy użyciu serializacji</span><span class="sxs-lookup"><span data-stu-id="1e36a-147">Using Serialization to Persist the Object</span></span>  
 <span data-ttu-id="1e36a-148">Aby zachować wartości dla klasy pożyczek, należy najpierw oznaczyć klasę `Serializable` atrybutem.</span><span class="sxs-lookup"><span data-stu-id="1e36a-148">In order to persist the values for the Loan class, you must first mark the class with the `Serializable` attribute.</span></span>  
  
### <a name="to-mark-a-class-as-serializable"></a><span data-ttu-id="1e36a-149">Aby oznaczyć klasę jako możliwy do serializacji</span><span class="sxs-lookup"><span data-stu-id="1e36a-149">To mark a class as serializable</span></span>  
  
- <span data-ttu-id="1e36a-150">Zmień deklarację klasy dla klasy pożyczek w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1e36a-150">Change the class declaration for the Loan class as follows:</span></span>  
  
    ```vb  
    <Serializable()>  
    Public Class Loan  
    ```  
  
 <span data-ttu-id="1e36a-151">Ten `Serializable` atrybut informuje kompilator, że wszystko w klasie może być utrwalone w pliku.</span><span class="sxs-lookup"><span data-stu-id="1e36a-151">The `Serializable` attribute tells the compiler that everything in the class can be persisted to a file.</span></span> <span data-ttu-id="1e36a-152">`PropertyChanged` Ponieważ zdarzenie jest obsługiwane przez obiekt formularza systemu Windows, nie może być serializowane.</span><span class="sxs-lookup"><span data-stu-id="1e36a-152">Because the `PropertyChanged` event is handled by a Windows Form object, it cannot be serialized.</span></span> <span data-ttu-id="1e36a-153">Ten `NonSerialized` atrybut może służyć do oznaczania elementów członkowskich klasy, które nie powinny być utrwalane.</span><span class="sxs-lookup"><span data-stu-id="1e36a-153">The `NonSerialized` attribute can be used to mark class members that should not be persisted.</span></span>  
  
### <a name="to-prevent-a-member-from-being-serialized"></a><span data-ttu-id="1e36a-154">Aby zapobiec serializacji elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="1e36a-154">To prevent a member from being serialized</span></span>  
  
- <span data-ttu-id="1e36a-155">Zmień deklarację dla `PropertyChanged` zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1e36a-155">Change the declaration for the `PropertyChanged` event as follows:</span></span>  
  
    ```vb  
    <NonSerialized()>  
    Event PropertyChanged As System.ComponentModel.PropertyChangedEventHandler _  
      Implements System.ComponentModel.INotifyPropertyChanged.PropertyChanged  
    ```  
  
 <span data-ttu-id="1e36a-156">Następnym krokiem jest dodanie kodu serializacji do aplikacji LoanApp.</span><span class="sxs-lookup"><span data-stu-id="1e36a-156">The next step is to add the serialization code to the LoanApp application.</span></span> <span data-ttu-id="1e36a-157">Aby serializować klasę i zapisać ją w pliku, należy użyć <xref:System.IO> przestrzeni nazw i. <xref:System.Xml.Serialization></span><span class="sxs-lookup"><span data-stu-id="1e36a-157">In order to serialize the class and write it to a file, you will use the <xref:System.IO> and <xref:System.Xml.Serialization> namespaces.</span></span> <span data-ttu-id="1e36a-158">Aby uniknąć wpisywania w pełni kwalifikowanych nazw, można dodać odwołania do niezbędnych bibliotek klas.</span><span class="sxs-lookup"><span data-stu-id="1e36a-158">To avoid typing the fully qualified names, you can add references to the necessary class libraries.</span></span>  
  
### <a name="to-add-references-to-namespaces"></a><span data-ttu-id="1e36a-159">Aby dodać odwołania do przestrzeni nazw</span><span class="sxs-lookup"><span data-stu-id="1e36a-159">To add references to namespaces</span></span>  
  
- <span data-ttu-id="1e36a-160">Dodaj następujące instrukcje na górze `Form1` klasy:</span><span class="sxs-lookup"><span data-stu-id="1e36a-160">Add the following statements to the top of the `Form1` class:</span></span>  
  
    ```vb  
    Imports System.IO  
    Imports System.Runtime.Serialization.Formatters.Binary  
    ```  
  
     <span data-ttu-id="1e36a-161">W takim przypadku używasz pliku binarnego programu formatującego do zapisania obiektu w formacie binarnym.</span><span class="sxs-lookup"><span data-stu-id="1e36a-161">In this case, you are using a binary formatter to save the object in a binary format.</span></span>  
  
 <span data-ttu-id="1e36a-162">Następnym krokiem jest dodanie kodu w celu deserializacji obiektu z pliku po utworzeniu obiektu.</span><span class="sxs-lookup"><span data-stu-id="1e36a-162">The next step is to add code to deserialize the object from the file when the object is created.</span></span>  
  
### <a name="to-deserialize-an-object"></a><span data-ttu-id="1e36a-163">Do deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="1e36a-163">To deserialize an object</span></span>  
  
1. <span data-ttu-id="1e36a-164">Dodaj stałą do klasy dla nazwy pliku serializowanej danych.</span><span class="sxs-lookup"><span data-stu-id="1e36a-164">Add a constant to the class for the serialized data's file name.</span></span>  
  
    ```vb  
    Const FileName As String = "..\..\SavedLoan.bin"  
    ```  
  
2. <span data-ttu-id="1e36a-165">Zmodyfikuj kod w `Form1_Load` procedurze zdarzenia w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="1e36a-165">Modify the code in the `Form1_Load` event procedure as follows:</span></span>  
  
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
  
     <span data-ttu-id="1e36a-166">Należy pamiętać, że najpierw należy sprawdzić, czy plik istnieje.</span><span class="sxs-lookup"><span data-stu-id="1e36a-166">Note that you first must check that the file exists.</span></span> <span data-ttu-id="1e36a-167">Jeśli istnieje, Utwórz <xref:System.IO.Stream> klasę, aby odczytać plik binarny <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> i klasę, aby przetłumaczyć plik.</span><span class="sxs-lookup"><span data-stu-id="1e36a-167">If it exists, create a <xref:System.IO.Stream> class to read the binary file and a <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter> class to translate the file.</span></span> <span data-ttu-id="1e36a-168">Należy również przekonwertować typ strumienia na typ obiektu pożyczki.</span><span class="sxs-lookup"><span data-stu-id="1e36a-168">You also need to convert from the stream type to the Loan object type.</span></span>  
  
 <span data-ttu-id="1e36a-169">Następnie musisz dodać kod, aby zapisać dane wprowadzone w polach tekstowych do `Loan` klasy, a następnie trzeba serializować klasę do pliku.</span><span class="sxs-lookup"><span data-stu-id="1e36a-169">Next you must add code to save the data entered in the text boxes to the `Loan` class, and then you must serialize the class to a file.</span></span>  
  
### <a name="to-save-the-data-and-serialize-the-class"></a><span data-ttu-id="1e36a-170">Aby zapisać dane i serializować klasę</span><span class="sxs-lookup"><span data-stu-id="1e36a-170">To save the data and serialize the class</span></span>  
  
- <span data-ttu-id="1e36a-171">Dodaj następujący kod do `Form1_FormClosing` procedury zdarzenia:</span><span class="sxs-lookup"><span data-stu-id="1e36a-171">Add the following code to the `Form1_FormClosing` event procedure:</span></span>  
  
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
  
 <span data-ttu-id="1e36a-172">W tym momencie możesz ponownie skompilować i uruchomić aplikację.</span><span class="sxs-lookup"><span data-stu-id="1e36a-172">At this point, you can again build and run the application.</span></span> <span data-ttu-id="1e36a-173">Początkowo wartości domyślne pojawiają się w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="1e36a-173">Initially, the default values appear in the text boxes.</span></span> <span data-ttu-id="1e36a-174">Spróbuj zmienić wartości i wprowadź nazwę w czwartym polu tekstowym.</span><span class="sxs-lookup"><span data-stu-id="1e36a-174">Try to change the values and enter a name in the fourth text box.</span></span> <span data-ttu-id="1e36a-175">Zamknij aplikację, a następnie uruchom ją ponownie.</span><span class="sxs-lookup"><span data-stu-id="1e36a-175">Close the application and then run it again.</span></span> <span data-ttu-id="1e36a-176">Należy pamiętać, że nowe wartości są teraz wyświetlane w polach tekstowych.</span><span class="sxs-lookup"><span data-stu-id="1e36a-176">Note that the new values now appear in the text boxes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e36a-177">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1e36a-177">See also</span></span>

- [<span data-ttu-id="1e36a-178">Serializacja (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="1e36a-178">Serialization (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/serialization/index.md)
- [<span data-ttu-id="1e36a-179">Przewodnik programowania Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1e36a-179">Visual Basic Programming Guide</span></span>](../../../../visual-basic/programming-guide/index.md)
