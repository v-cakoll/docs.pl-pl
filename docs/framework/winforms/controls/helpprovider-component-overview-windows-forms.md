---
title: HelpProvider — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- HelpProvider
helpviewer_keywords:
- HelpProvider component [Windows Forms], about HelpProvider component
- Help [Windows Forms], adding to Windows applications
- F1 Help [Windows Forms], adding to Windows Forms
- dialog boxes [Windows Forms], context-sensitive Help
- Windows Forms, context-sensitive Help
ms.assetid: 6b10c2cc-c577-4cb5-9669-e37b33416af9
ms.openlocfilehash: cefc590bb3011b282392504a78ac5c393c58493e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965693"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="04bd4-102">HelpProvider — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="04bd4-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="04bd4-103">Windows Forms składnik [HelpProvider —](helpprovider-component-windows-forms.md) służy do kojarzenia pliku pomocy HTML pomocy 1. x (plik. chm, utworzony za pomocą programu HTML Help Workshop lub pliku. htm) z aplikacją systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="04bd4-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="04bd4-104">Możesz zapewnić pomoc na różne sposoby:</span><span class="sxs-lookup"><span data-stu-id="04bd4-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="04bd4-105">Zapewnianie pomocy kontekstowej dla formantów na Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="04bd4-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="04bd4-106">Zapewnianie pomocy kontekstowej w konkretnym oknie dialogowym lub określonych kontrolkach w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="04bd4-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="04bd4-107">Otwórz plik pomocy do określonych obszarów, takich jak Strona główna spisu treści, indeks lub funkcja wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="04bd4-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="04bd4-108">Korzystanie z dostawcy pomocy</span><span class="sxs-lookup"><span data-stu-id="04bd4-108">Using the Help Provider</span></span>  
 <span data-ttu-id="04bd4-109">Dodanie składnika do formularza systemu Windows umożliwia innym kontrolom w formularzu uwidocznienie właściwości <xref:System.Windows.Forms.HelpProvider> pomocy składnika. <xref:System.Windows.Forms.HelpProvider></span><span class="sxs-lookup"><span data-stu-id="04bd4-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="04bd4-110">Dzięki temu można zapewnić pomoc dla kontrolek w formularzu systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="04bd4-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="04bd4-111">Można skojarzyć plik pomocy ze <xref:System.Windows.Forms.HelpProvider> składnikiem <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> za pomocą właściwości.</span><span class="sxs-lookup"><span data-stu-id="04bd4-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="04bd4-112">Należy określić typ pomocy zapewnianej przez wywoływanie <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podanie wartości <xref:System.Windows.Forms.HelpNavigator> z wyliczenia dla określonej kontrolki.</span><span class="sxs-lookup"><span data-stu-id="04bd4-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="04bd4-113">Podajesz słowo kluczowe lub temat pomocy, wywołując <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="04bd4-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="04bd4-114">Opcjonalnie, aby skojarzyć określony ciąg pomocy z inną kontrolką, użyj <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="04bd4-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="04bd4-115">Ciąg, który można skojarzyć z kontrolką przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy kontrolka ma fokus.</span><span class="sxs-lookup"><span data-stu-id="04bd4-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="04bd4-116">Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie została ustawiona, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> , aby podać tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="04bd4-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="04bd4-117">Jeśli ustawiono oba <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> parametry i ciąg pomocy, pierwszeństwo <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> ma pomoc na podstawie.</span><span class="sxs-lookup"><span data-stu-id="04bd4-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="04bd4-118">Podczas określania ścieżki do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metodzie lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości <xref:System.Windows.Forms.HelpProvider> formantu mogą wystąpić problemy przy użyciu ścieżki względnej.</span><span class="sxs-lookup"><span data-stu-id="04bd4-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="04bd4-119">W związku z tym Pamiętaj o określeniu pliku pomocy za pomocą bezwzględnej ścieżki pliku.</span><span class="sxs-lookup"><span data-stu-id="04bd4-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="04bd4-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04bd4-120">See also</span></span>

- [<span data-ttu-id="04bd4-121">Systemy Pomocy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="04bd4-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
