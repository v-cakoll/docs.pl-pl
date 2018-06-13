---
title: 'Porady: wyświetlanie dostępnych portów seryjnych w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c13682ddca69d782ea519e0df703c211df8d12c4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33586728"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="1fc73-102">Porady: wyświetlanie dostępnych portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="1fc73-102">How to: Show Available Serial Ports in Visual Basic</span></span>
<span data-ttu-id="1fc73-103">W tym temacie opisano sposób użycia `My.Computer.Ports` Aby wyświetlić dostępne porty szeregowe komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="1fc73-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="1fc73-104">Umożliwia użytkownikowi wybranie port, który można użyć nazwy porty szeregowe są umieszczane w <xref:System.Windows.Forms.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="1fc73-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1fc73-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1fc73-105">Example</span></span>  
 <span data-ttu-id="1fc73-106">W tym przykładzie pętli wszystkie ciągi który `My.Computer.Ports.SerialPortNames` zwraca właściwości.</span><span class="sxs-lookup"><span data-stu-id="1fc73-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="1fc73-107">Te parametry są nazwami dostępne porty szeregowe na komputerze.</span><span class="sxs-lookup"><span data-stu-id="1fc73-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="1fc73-108">Zazwyczaj użytkownik wybiera które portu szeregowego należy używać aplikacji z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="1fc73-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="1fc73-109">W tym przykładzie nazwy portu szeregowego są przechowywane w <xref:System.Windows.Forms.ListBox> formantu.</span><span class="sxs-lookup"><span data-stu-id="1fc73-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="1fc73-110">Aby uzyskać więcej informacji, zobacz [kontrolki ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="1fc73-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](../../../../visual-basic/developing-apps/programming/computer-resources/codesnippet/VisualBasic/how-to-show-available-serial-ports_1.vb)]  
  
 <span data-ttu-id="1fc73-111">W tym przykładzie kodu jest również dostępny jako fragmentu kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1fc73-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="1fc73-112">Selektor wstawek kodu, znajduje się się w **sieć i łączność**.</span><span class="sxs-lookup"><span data-stu-id="1fc73-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="1fc73-113">Aby uzyskać więcej informacji, zobacz [wstawki kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="1fc73-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1fc73-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1fc73-114">Compiling the Code</span></span>  
 <span data-ttu-id="1fc73-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1fc73-115">This example requires:</span></span>  
  
-   <span data-ttu-id="1fc73-116">Odwołanie projektu do System.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="1fc73-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
-   <span data-ttu-id="1fc73-117">Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="1fc73-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="1fc73-118">Dodaj `Imports` instrukcję, jeśli użytkownik jest całkowicie niekwalifikujących nazwy elementów członkowskich w kodzie.</span><span class="sxs-lookup"><span data-stu-id="1fc73-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="1fc73-119">Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (.NET Namespace i Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="1fc73-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
-   <span data-ttu-id="1fc73-120">Formularz zainstalowanego <xref:System.Windows.Forms.ListBox> formantu o nazwie `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="1fc73-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="1fc73-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="1fc73-121">Robust Programming</span></span>  
 <span data-ttu-id="1fc73-122">Nie trzeba używać <xref:System.Windows.Forms.ListBox> formantu, aby wyświetlić nazwy dostępnego portu szeregowego.</span><span class="sxs-lookup"><span data-stu-id="1fc73-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="1fc73-123">Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub inny formant.</span><span class="sxs-lookup"><span data-stu-id="1fc73-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="1fc73-124">Jeśli aplikacja nie wymaga odpowiedzi od użytkownika, możesz użyć <xref:System.Windows.Forms.TextBox> formantu, aby wyświetlić informacje.</span><span class="sxs-lookup"><span data-stu-id="1fc73-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1fc73-125">Nazwy portów zwrócony przez `My.Computer.Ports.SerialPortNames` może być niepoprawna uruchomienia w systemach Windows 98.</span><span class="sxs-lookup"><span data-stu-id="1fc73-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="1fc73-126">Aby zapobiec błędom aplikacji, użyj obsługi wyjątków, takich jak `Try...Catch...Finally` instrukcji lub `Using` instrukcji, gdy używane są nazwy portu otworzyć porty.</span><span class="sxs-lookup"><span data-stu-id="1fc73-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1fc73-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1fc73-127">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Devices.Ports>  
 [<span data-ttu-id="1fc73-128">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="1fc73-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)  
 [<span data-ttu-id="1fc73-129">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="1fc73-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)  
 [<span data-ttu-id="1fc73-130">Instrukcje: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="1fc73-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
