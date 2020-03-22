---
title: 'Porady: wyświetlanie dostępnych portów seryjnych'
ms.date: 07/20/2015
helpviewer_keywords:
- serial ports, availability
- My.Computer.Ports.SerialPortNames property
- My.Computer.Ports object
- ports, serial port availability
ms.assetid: eaf2ee5a-8103-4e10-a205-ed1d4db120ba
ms.openlocfilehash: c7e5f797c1d098a3b2d01745b949ed50375ea7e8
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74345573"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="6cc93-102">Porady: wyświetlanie dostępnych portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="6cc93-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="6cc93-103">W tym temacie `My.Computer.Ports` opisano sposób używania do pokazywalenia dostępnych portów szeregowych komputera w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="6cc93-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="6cc93-104">Aby umożliwić użytkownikowi wybranie portu, którego ma być używany, <xref:System.Windows.Forms.ListBox> nazwy portów szeregowych są umieszczane w formancie.</span><span class="sxs-lookup"><span data-stu-id="6cc93-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6cc93-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="6cc93-105">Example</span></span>  

 <span data-ttu-id="6cc93-106">W tym przykładzie pętli na `My.Computer.Ports.SerialPortNames` wszystkie ciągi, które zwraca właściwość.</span><span class="sxs-lookup"><span data-stu-id="6cc93-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="6cc93-107">Te ciągi są nazwami dostępnych portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6cc93-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="6cc93-108">Zazwyczaj użytkownik wybiera port szeregowy, którego aplikacja powinna używać z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="6cc93-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="6cc93-109">W tym przykładzie nazwy portów <xref:System.Windows.Forms.ListBox> szeregowych są przechowywane w formancie.</span><span class="sxs-lookup"><span data-stu-id="6cc93-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="6cc93-110">Aby uzyskać więcej informacji, zobacz [Formant pola list](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="6cc93-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="6cc93-111">W tym przykładzie kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="6cc93-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="6cc93-112">W selektorze fragmentów kodu znajduje się w **sekcji Łączność i sieć**.</span><span class="sxs-lookup"><span data-stu-id="6cc93-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="6cc93-113">Aby uzyskać więcej informacji, zobacz [Fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="6cc93-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="6cc93-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="6cc93-114">Compiling the Code</span></span>  

 <span data-ttu-id="6cc93-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="6cc93-115">This example requires:</span></span>  
  
- <span data-ttu-id="6cc93-116">Odwołanie do projektu system.Windows.Forms.dll.</span><span class="sxs-lookup"><span data-stu-id="6cc93-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="6cc93-117">Dostęp do członków <xref:System.Windows.Forms> obszaru nazw.</span><span class="sxs-lookup"><span data-stu-id="6cc93-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="6cc93-118">Dodaj `Imports` instrukcję, jeśli nie są w pełni kwalifikujące się nazwy członków w kodzie.</span><span class="sxs-lookup"><span data-stu-id="6cc93-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="6cc93-119">Aby uzyskać więcej informacji, zobacz [Oświadczenie importu (.NET Obszar nazw i Typ)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="6cc93-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="6cc93-120">Aby formularz miał <xref:System.Windows.Forms.ListBox> formant o nazwie `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="6cc93-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="6cc93-121">Niezawodne programowanie</span><span class="sxs-lookup"><span data-stu-id="6cc93-121">Robust Programming</span></span>  

 <span data-ttu-id="6cc93-122">Nie trzeba używać formantu do <xref:System.Windows.Forms.ListBox> wyświetlania dostępnych nazw portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="6cc93-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="6cc93-123">Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub innego formantu.</span><span class="sxs-lookup"><span data-stu-id="6cc93-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="6cc93-124">Jeśli aplikacja nie potrzebuje odpowiedzi od użytkownika, można <xref:System.Windows.Forms.TextBox> użyć formantu do wyświetlania informacji.</span><span class="sxs-lookup"><span data-stu-id="6cc93-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6cc93-125">Nazwy portów `My.Computer.Ports.SerialPortNames` zwrócone przez mogą być niepoprawne podczas uruchamiania w systemie Windows 98.</span><span class="sxs-lookup"><span data-stu-id="6cc93-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="6cc93-126">Aby zapobiec błędom aplikacji, należy użyć `Try...Catch...Finally` obsługi `Using` wyjątków, takich jak instrukcja lub instrukcja, podczas używania nazw portów do otwierania portów.</span><span class="sxs-lookup"><span data-stu-id="6cc93-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6cc93-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6cc93-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="6cc93-128">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="6cc93-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="6cc93-129">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="6cc93-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="6cc93-130">Instrukcje: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="6cc93-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
