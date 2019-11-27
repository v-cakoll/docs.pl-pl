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
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345573"
---
# <a name="how-to-show-available-serial-ports-in-visual-basic"></a><span data-ttu-id="4a6b6-102">Porady: wyświetlanie dostępnych portów seryjnych w Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4a6b6-102">How to: Show Available Serial Ports in Visual Basic</span></span>

<span data-ttu-id="4a6b6-103">W tym temacie opisano, jak używać `My.Computer.Ports` do wyświetlania dostępnych portów szeregowych komputera w Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-103">This topic describes how to use `My.Computer.Ports` to show the available serial ports of the computer in Visual Basic.</span></span>  
  
 <span data-ttu-id="4a6b6-104">Aby umożliwić użytkownikowi wybranie portu do użycia, nazwy portów szeregowych są umieszczane w kontrolce <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-104">To allow a user to select which port to use, the names of the serial ports are placed in a <xref:System.Windows.Forms.ListBox> control.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4a6b6-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="4a6b6-105">Example</span></span>  

 <span data-ttu-id="4a6b6-106">Ten przykład pętli dla wszystkich ciągów zwracanych przez właściwość `My.Computer.Ports.SerialPortNames`.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-106">This example loops over all the strings that the `My.Computer.Ports.SerialPortNames` property returns.</span></span> <span data-ttu-id="4a6b6-107">Te ciągi są nazwami dostępnych portów szeregowych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-107">These strings are the names of the available serial ports on the computer.</span></span>  
  
 <span data-ttu-id="4a6b6-108">Zazwyczaj użytkownik wybiera port szeregowy, który ma być używany przez aplikację z listy dostępnych portów.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-108">Typically, a user selects which serial port the application should use from the list of available ports.</span></span> <span data-ttu-id="4a6b6-109">W tym przykładzie nazwy portów szeregowych są przechowywane w kontrolce <xref:System.Windows.Forms.ListBox>.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-109">In this example, the serial port names are stored in a <xref:System.Windows.Forms.ListBox> control.</span></span> <span data-ttu-id="4a6b6-110">Aby uzyskać więcej informacji, zobacz [formant ListBox](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4a6b6-110">For more information, see [ListBox Control](../../../../framework/winforms/controls/listbox-control-windows-forms.md).</span></span>  
  
 [!code-vb[VbVbalrMyComputer#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrMyComputer/VB/Class2.vb#45)]  
  
 <span data-ttu-id="4a6b6-111">Ten przykład kodu jest również dostępny jako fragment kodu IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-111">This code example is also available as an IntelliSense code snippet.</span></span> <span data-ttu-id="4a6b6-112">W selektorze fragmentów kodu znajdują się one w obszarze **łączności i sieci**.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-112">In the code snippet picker, it is located in **Connectivity and Networking**.</span></span> <span data-ttu-id="4a6b6-113">Aby uzyskać więcej informacji, zobacz [fragmenty kodu](/visualstudio/ide/code-snippets).</span><span class="sxs-lookup"><span data-stu-id="4a6b6-113">For more information, see [Code Snippets](/visualstudio/ide/code-snippets).</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4a6b6-114">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="4a6b6-114">Compiling the Code</span></span>  

 <span data-ttu-id="4a6b6-115">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="4a6b6-115">This example requires:</span></span>  
  
- <span data-ttu-id="4a6b6-116">Odwołanie do projektu do System. Windows. Forms. dll.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-116">A project reference to System.Windows.Forms.dll.</span></span>  
  
- <span data-ttu-id="4a6b6-117">Dostęp do elementów członkowskich <xref:System.Windows.Forms> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-117">Access to the members of the <xref:System.Windows.Forms> namespace.</span></span> <span data-ttu-id="4a6b6-118">Dodaj instrukcję `Imports`, jeśli nie masz w pełni kwalifikowanej nazwy elementu członkowskiego w kodzie.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-118">Add an `Imports` statement if you are not fully qualifying member names in your code.</span></span> <span data-ttu-id="4a6b6-119">Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw i typ .NET)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span><span class="sxs-lookup"><span data-stu-id="4a6b6-119">For more information, see [Imports Statement (.NET Namespace and Type)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).</span></span>  
  
- <span data-ttu-id="4a6b6-120">Że formularz zawiera kontrolkę <xref:System.Windows.Forms.ListBox> o nazwie `ListBox1`.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-120">That your form have a <xref:System.Windows.Forms.ListBox> control named `ListBox1`.</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="4a6b6-121">Skuteczne programowanie</span><span class="sxs-lookup"><span data-stu-id="4a6b6-121">Robust Programming</span></span>  

 <span data-ttu-id="4a6b6-122">Nie trzeba używać kontrolki <xref:System.Windows.Forms.ListBox> do wyświetlania dostępnych nazw portów szeregowych.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-122">You do not have to use the <xref:System.Windows.Forms.ListBox> control to display the available serial port names.</span></span> <span data-ttu-id="4a6b6-123">Zamiast tego można użyć <xref:System.Windows.Forms.ComboBox> lub innej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-123">Instead, you can use a <xref:System.Windows.Forms.ComboBox> or other control.</span></span> <span data-ttu-id="4a6b6-124">Jeśli aplikacja nie potrzebuje odpowiedzi od użytkownika, można użyć kontrolki <xref:System.Windows.Forms.TextBox>, aby wyświetlić informacje.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-124">If the application does not need a response from the user, you can use a <xref:System.Windows.Forms.TextBox> control to display the information.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4a6b6-125">Nazwy portów zwracane przez `My.Computer.Ports.SerialPortNames` mogą być nieprawidłowe w przypadku uruchomienia w systemie Windows 98.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-125">The port names returned by `My.Computer.Ports.SerialPortNames` may be incorrect when run on Windows 98.</span></span> <span data-ttu-id="4a6b6-126">Aby zapobiec błędom aplikacji, należy użyć obsługi wyjątków, na przykład instrukcji `Try...Catch...Finally` lub instrukcji `Using`, w przypadku używania nazw portów do otwierania portów.</span><span class="sxs-lookup"><span data-stu-id="4a6b6-126">To prevent application errors, use exception handling, such as the `Try...Catch...Finally` statement or the `Using` statement, when using the port names to open ports.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4a6b6-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4a6b6-127">See also</span></span>

- <xref:Microsoft.VisualBasic.Devices.Ports>
- [<span data-ttu-id="4a6b6-128">Instrukcje: modemy dostępowe powiązane z portami seryjnymi</span><span class="sxs-lookup"><span data-stu-id="4a6b6-128">How to: Dial Modems Attached to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-dial-modems-attached-to-serial-ports.md)
- [<span data-ttu-id="4a6b6-129">Instrukcje: wysyłanie ciągów do portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="4a6b6-129">How to: Send Strings to Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-send-strings-to-serial-ports.md)
- [<span data-ttu-id="4a6b6-130">Instrukcje: odbieranie ciągów z portów seryjnych</span><span class="sxs-lookup"><span data-stu-id="4a6b6-130">How to: Receive Strings From Serial Ports</span></span>](../../../../visual-basic/developing-apps/programming/computer-resources/how-to-receive-strings-from-serial-ports.md)
