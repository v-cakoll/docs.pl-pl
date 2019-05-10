---
title: 'Instrukcje: Wyświetlanie dostępnych portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: d6b092b499af2003e8a43987677b13741c362b1b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662709"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="38ee4-102">Instrukcje: Wyświetlanie dostępnych portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="38ee4-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="38ee4-103">W tym temacie opisano sposób użycia `My.Computer.Ports` Aby wyświetlić dostępne porty szeregowe komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="38ee4-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="38ee4-104">Aby zezwolić na port, który umożliwia wybranie użytkownika, nazwy portów szeregowych są umieszczane w <xref:System.Windows.Forms.ListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38ee4-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="38ee4-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="38ee4-105">Example</span></span>  
 <span data-ttu-id="38ee4-106">W tym przykładzie pętli wszystkich ciągów, `My.Computer.Ports.SerialPortNames` zwraca właściwości.</span><span class="sxs-lookup"><span data-stu-id="38ee4-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="38ee4-107">Te ciągi są nazwy dostępnych portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="38ee4-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="38ee4-108">Zazwyczaj użytkownik wybierze które portu szeregowego, należy użyć aplikacji z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="38ee4-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="38ee4-109">W tym przykładzie nazwy portu szeregowego są przechowywane w <xref:System.Windows.Forms.ListBox> kontroli.</span><span class="sxs-lookup"><span data-stu-id="38ee4-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="38ee4-110">Aby uzyskać więcej informacji, zobacz [kontrolki ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="38ee4-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="38ee4-111">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="38ee4-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="38ee4-112">W selektorze fragmentów kodu, znajduje się w **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="38ee4-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="38ee4-113">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="38ee4-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="38ee4-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="38ee4-114">Compiling the Code</span></span>  
 <span data-ttu-id="38ee4-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="38ee4-115">This example requires:</span></span>  
  
- <span data-ttu-id="38ee4-116">Odwołanie projektu do pliku System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="38ee4-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="38ee4-117">Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="38ee4-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="38ee4-118">Dodaj `Imports` instrukcji, jeśli użytkownik są nie pełni kwalifikujących się nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="38ee4-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="38ee4-119">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="38ee4-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="38ee4-120">Mających formularza <xref:System.Windows.Forms.ListBox> formantu o nazwie `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="38ee4-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="38ee4-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="38ee4-121">Robust Programming</span></span>  
 <span data-ttu-id="38ee4-122">Nie trzeba używać <xref:System.Windows.Forms.ListBox> formantu, aby wyświetlić nazwy dostępnych portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="38ee4-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="38ee4-123">Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub inny formant.</span><span class="sxs-lookup"><span data-stu-id="38ee4-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="38ee4-124">Jeśli aplikacja nie wymaga odpowiedź od użytkownika, możesz użyć <xref:System.Windows.Forms.TextBox> formantu, aby wyświetlić informacje.</span><span class="sxs-lookup"><span data-stu-id="38ee4-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="38ee4-125">Nazwy portu zwrócony przez `My.Computer.Ports.SerialPortNames` mogą być niepoprawne uruchamiania Windows 98.</span><span class="sxs-lookup"><span data-stu-id="38ee4-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="38ee4-126">Aby uniknąć błędów aplikacji, należy użyć obsługi wyjątków, takie jak `Try...Catch...Finally` instrukcji lub `Using` instrukcji, gdy używane są nazwy portu umożliwiające otwarcie portów.</span><span class="sxs-lookup"><span data-stu-id="38ee4-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38ee4-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="38ee4-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="38ee4-128">Instrukcje: Modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="38ee4-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="38ee4-129">Instrukcje: Wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="38ee4-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="38ee4-130">Instrukcje: Odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="38ee4-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
