---
title: 'Porady: zapewnianie pomocy w aplikacji Windows'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help [Windows Forms], Windows applications
- HTML Help [Windows Forms], Windows Forms
- Windows applications [Windows Forms], providing Help
- HelpProvider component [Windows Forms]
- forms [Windows Forms], providing Help
ms.assetid: 7c4e5cec-2bd2-4f0b-8d75-c2b88929bd61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0f407f1c17c67ec99f4499b89c49932a4ba6d32c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-provide-help-in-a-windows-application"></a><span data-ttu-id="b17aa-102">Porady: zapewnianie pomocy w aplikacji Windows</span><span class="sxs-lookup"><span data-stu-id="b17aa-102">How to: Provide Help in a Windows Application</span></span>
<span data-ttu-id="b17aa-103">Można również użyć <xref:System.Windows.Forms.HelpProvider> składnika można dołączyć tematów pomocy w pliku pomocy do określonych formantów na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b17aa-103">You can use of the <xref:System.Windows.Forms.HelpProvider> component to attach Help topics within a Help file to specific controls on Windows Forms.</span></span> <span data-ttu-id="b17aa-104">Może to być plik Pomocy HTML lub HTMLHelp 1.x lub format większa.</span><span class="sxs-lookup"><span data-stu-id="b17aa-104">The Help file can be either HTML or HTMLHelp 1.x or greater format.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b17aa-105">Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania.</span><span class="sxs-lookup"><span data-stu-id="b17aa-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="b17aa-106">Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu.</span><span class="sxs-lookup"><span data-stu-id="b17aa-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="b17aa-107">Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="b17aa-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-provide-help"></a><span data-ttu-id="b17aa-108">Aby zapewnić pomoc</span><span class="sxs-lookup"><span data-stu-id="b17aa-108">To provide Help</span></span>  
  
1.  <span data-ttu-id="b17aa-109">Z **przybornika**, przeciągnij <xref:System.Windows.Forms.HelpProvider> składnika do formularza.</span><span class="sxs-lookup"><span data-stu-id="b17aa-109">From the **Toolbox**, drag a <xref:System.Windows.Forms.HelpProvider> component to your form.</span></span>  
  
     <span data-ttu-id="b17aa-110">Składnik będą znajdować się w pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b17aa-110">The component will reside in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="b17aa-111">W **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości .chm, .col lub .htm pliku pomocy.</span><span class="sxs-lookup"><span data-stu-id="b17aa-111">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property to the .chm, .col, or .htm Help file.</span></span>  
  
3.  <span data-ttu-id="b17aa-112">Wybierz inny formant na formularzu, a następnie w **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="b17aa-112">Select another control you have on your form, and in the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> property.</span></span>  
  
     <span data-ttu-id="b17aa-113">Jest to ciąg przekazywane <xref:System.Windows.Forms.HelpProvider> składnika do pliku pomocy wezwać odpowiedniego tematu Pomocy.</span><span class="sxs-lookup"><span data-stu-id="b17aa-113">This is the string passed through the <xref:System.Windows.Forms.HelpProvider> component to your Help file to summon the appropriate Help topic.</span></span>  
  
4.  <span data-ttu-id="b17aa-114">W **właściwości** ustaw <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> właściwości na wartość <xref:System.Windows.Forms.HelpNavigator> wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="b17aa-114">In the **Properties** window, set the <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> property to a value of the <xref:System.Windows.Forms.HelpNavigator> enumeration.</span></span>  
  
     <span data-ttu-id="b17aa-115">Określa sposób, w którym **HelpKeyword** właściwość jest przekazywana do systemu pomocy.</span><span class="sxs-lookup"><span data-stu-id="b17aa-115">This determines the way in which the **HelpKeyword** property is passed to the Help system.</span></span> <span data-ttu-id="b17aa-116">W poniższej tabeli przedstawiono ustawienia możliwe i ich opisy.</span><span class="sxs-lookup"><span data-stu-id="b17aa-116">The following table shows the possible settings and their descriptions.</span></span>  
  
    |<span data-ttu-id="b17aa-117">Nazwa elementu członkowskiego</span><span class="sxs-lookup"><span data-stu-id="b17aa-117">Member Name</span></span>|<span data-ttu-id="b17aa-118">Opis</span><span class="sxs-lookup"><span data-stu-id="b17aa-118">Description</span></span>|  
    |-----------------|-----------------|  
    |<span data-ttu-id="b17aa-119">AssociateIndex</span><span class="sxs-lookup"><span data-stu-id="b17aa-119">AssociateIndex</span></span>|<span data-ttu-id="b17aa-120">Określa, czy indeksu dla określonego tematu jest wykonywana w określonym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="b17aa-120">Specifies that the index for a specified topic is performed in the specified URL.</span></span>|  
    |<span data-ttu-id="b17aa-121">Znajdź</span><span class="sxs-lookup"><span data-stu-id="b17aa-121">Find</span></span>|<span data-ttu-id="b17aa-122">Określa, czy są wyświetlane na stronie wyszukiwania określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="b17aa-122">Specifies that the search page of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="b17aa-123">Indeks</span><span class="sxs-lookup"><span data-stu-id="b17aa-123">Index</span></span>|<span data-ttu-id="b17aa-124">Określa, czy jest wyświetlany indeks określonego adresu URL.</span><span class="sxs-lookup"><span data-stu-id="b17aa-124">Specifies that the index of a specified URL is displayed.</span></span>|  
    |<span data-ttu-id="b17aa-125">KeywordIndex</span><span class="sxs-lookup"><span data-stu-id="b17aa-125">KeywordIndex</span></span>|<span data-ttu-id="b17aa-126">Określa słowo kluczowe do wyszukania i działanie podejmowane w określonym adresem URL.</span><span class="sxs-lookup"><span data-stu-id="b17aa-126">Specifies a keyword to search for and the action to take in the specified URL.</span></span>|  
    |<span data-ttu-id="b17aa-127">TableOfContents</span><span class="sxs-lookup"><span data-stu-id="b17aa-127">TableOfContents</span></span>|<span data-ttu-id="b17aa-128">Określa, czy jest wyświetlany tabeli zawartość pliku Pomocy HTML 1.0.</span><span class="sxs-lookup"><span data-stu-id="b17aa-128">Specifies that the table of contents of the HTML 1.0 Help file is displayed.</span></span>|  
    |<span data-ttu-id="b17aa-129">Temat</span><span class="sxs-lookup"><span data-stu-id="b17aa-129">Topic</span></span>|<span data-ttu-id="b17aa-130">Określa, czy temat odwołuje się określony adres URL jest wyświetlana.</span><span class="sxs-lookup"><span data-stu-id="b17aa-130">Specifies that the topic referenced by the specified URL is displayed.</span></span>|  
  
 <span data-ttu-id="b17aa-131">W czasie wykonywania, naciskając klawisz F1 podczas kontroli — dla którego ustawiono **HelpKeyword** i **HelpNavigator** właściwości — ma fokus zostanie otwarty plik pomocy skojarzony z tym <xref:System.Windows.Forms.HelpProvider> składnika.</span><span class="sxs-lookup"><span data-stu-id="b17aa-131">At run time, pressing F1 when the control—for which you have set the **HelpKeyword** and **HelpNavigator** properties—has focus will open the Help file you associated with that <xref:System.Windows.Forms.HelpProvider> component.</span></span>  
  
 <span data-ttu-id="b17aa-132">Obecnie **HelpNamespace** właściwość obsługuje pliki pomocy w trzech następujących formatów: HTMLHelp 1.x, HTMLHelp 2.0 i HTML.</span><span class="sxs-lookup"><span data-stu-id="b17aa-132">Currently, the **HelpNamespace** property supports Help files in the following three formats: HTMLHelp 1.x, HTMLHelp 2.0, and HTML.</span></span> <span data-ttu-id="b17aa-133">W związku z tym można ustawić **HelpNamespace** właściwości adresu http://, takich jak strony sieci Web.</span><span class="sxs-lookup"><span data-stu-id="b17aa-133">Thus, you can set the **HelpNamespace** property to an http:// address, such as a Web page.</span></span> <span data-ttu-id="b17aa-134">Jeśli zostanie to zrobione, zostanie otwarty w domyślnej przeglądarce strony sieci Web z określonym w ciągu **HelpKeyword** właściwość używana jako swojej kotwicy.</span><span class="sxs-lookup"><span data-stu-id="b17aa-134">If this is done, it will open the default browser to the Web page with the string specified in the **HelpKeyword** property used as the anchor.</span></span> <span data-ttu-id="b17aa-135">Zakotwiczenia umożliwia przejście do określonej części strony HTML.</span><span class="sxs-lookup"><span data-stu-id="b17aa-135">The anchor is used to jump to a specific part of an HTML page.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b17aa-136">Należy zachować ostrożność sprawdzić wszystkie informacje, które są wysyłane przez klienta przed jego użyciem w aplikacji.</span><span class="sxs-lookup"><span data-stu-id="b17aa-136">Be careful to check any information that is sent from a client before using it in your application.</span></span> <span data-ttu-id="b17aa-137">Złośliwi użytkownicy mogą próbować wysyłać lub Wstaw skrypt pliku wykonywalnego, instrukcji SQL lub inny kod.</span><span class="sxs-lookup"><span data-stu-id="b17aa-137">Malicious users might try to send or inject executable script, SQL statements, or other code.</span></span> <span data-ttu-id="b17aa-138">Przed wyświetlania danych wprowadzonych przez użytkownika, zapisz go w bazie danych lub pracę z nią, należy sprawdzić, czy nie zawiera informacji potencjalnie niebezpieczne.</span><span class="sxs-lookup"><span data-stu-id="b17aa-138">Before you display a user's input, store it in a database, or work with it, check that it does not contain potentially unsafe information.</span></span> <span data-ttu-id="b17aa-139">Typowym sposobem, aby sprawdzić, jest użycie wyrażenia regularnego wyszukiwanie słów kluczowych "Skrypt" podczas odbierania danych wejściowych od użytkownika.</span><span class="sxs-lookup"><span data-stu-id="b17aa-139">A typical way to check is to use a regular expression to look for keywords such as "SCRIPT" when you receive input from a user.</span></span>  
  
 <span data-ttu-id="b17aa-140">Można również użyć <xref:System.Windows.Forms.HelpProvider> składnik, aby wyświetlić Pomoc wyskakująca, nawet jeśli jest ona skonfigurowana do wyświetlania plików pomocy dla formantów na formularzach systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="b17aa-140">You can also use the <xref:System.Windows.Forms.HelpProvider> component to show pop-up Help, even if you have it configured to display Help files for the controls on your Windows Forms.</span></span> <span data-ttu-id="b17aa-141">Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie wyskakujących pomocy](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span><span class="sxs-lookup"><span data-stu-id="b17aa-141">For more information, see [How to: Display Pop-up Help](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b17aa-142">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b17aa-142">See Also</span></span>  
 [<span data-ttu-id="b17aa-143">Porady: wyświetlanie pomocy podręcznej</span><span class="sxs-lookup"><span data-stu-id="b17aa-143">How to: Display Pop-up Help</span></span>](../../../../docs/framework/winforms/advanced/how-to-display-pop-up-help.md)  
 [<span data-ttu-id="b17aa-144">Pomoc w kontroli używanie etykietek narzędzi</span><span class="sxs-lookup"><span data-stu-id="b17aa-144">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="b17aa-145">Integrowanie pomocy użytkownika w formularzach systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b17aa-145">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="b17aa-146">Formularze systemu Windows</span><span class="sxs-lookup"><span data-stu-id="b17aa-146">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
