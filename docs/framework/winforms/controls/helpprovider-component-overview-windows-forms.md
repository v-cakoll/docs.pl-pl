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
ms.openlocfilehash: 9e8dc2ee2773b26a7bfef1da209399a8b49de9ad
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624126"
---
# <a name="helpprovider-component-overview-windows-forms"></a><span data-ttu-id="2ce4f-102">HelpProvider — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="2ce4f-102">HelpProvider Component Overview (Windows Forms)</span></span>
<span data-ttu-id="2ce4f-103">Formularze Windows [HelpProvider](helpprovider-component-windows-forms.md) składnik jest używany do kojarzenia pomocy HTML 1.x pliku pomocy (plik chm z HTML Help Workshop, lub do pliku .htm) za pomocą aplikacji Windows.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-103">The Windows Forms [HelpProvider](helpprovider-component-windows-forms.md) component is used to associate an HTML Help 1.x Help file (either a .chm file, produced with the HTML Help Workshop, or an .htm file) with your Windows application.</span></span> <span data-ttu-id="2ce4f-104">Możesz podać pomoc na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="2ce4f-104">You can provide help in a variety of ways:</span></span>  
  
- <span data-ttu-id="2ce4f-105">Podaj pomocy kontekstowej dla kontrolek na formularzach Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-105">Provide context-sensitive Help for controls on Windows Forms.</span></span>  
  
- <span data-ttu-id="2ce4f-106">Zapewniają pomoc kontekstowa w szczególności okno dialogowe lub określonych kontrolek w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-106">Provide context-sensitive Help on a particular dialog box or specific controls on a dialog box.</span></span>  
  
- <span data-ttu-id="2ce4f-107">Otwórz plik pomocy do określonych obszarów, takich jak strony głównej w spisie treści, indeksu lub funkcję wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-107">Open a Help file to specific areas, such as the main page of a Table of Contents, the Index, or a search function.</span></span>  
  
## <a name="using-the-help-provider"></a><span data-ttu-id="2ce4f-108">Za pomocą dostawcy pomocy</span><span class="sxs-lookup"><span data-stu-id="2ce4f-108">Using the Help Provider</span></span>  
 <span data-ttu-id="2ce4f-109">Dodawanie <xref:System.Windows.Forms.HelpProvider> składnik do formularza Windows umożliwia inne kontrolki na formularzu, należy udostępnić właściwości pomocy <xref:System.Windows.Forms.HelpProvider> składnika.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-109">Adding a <xref:System.Windows.Forms.HelpProvider> component to your Windows Form allows the other controls on the form to expose the Help properties of the <xref:System.Windows.Forms.HelpProvider> component.</span></span> <span data-ttu-id="2ce4f-110">Dzięki temu można zapewnić pomoc dla formantów w formularzu Windows.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-110">This enables you to provide help for the controls on your Windows Form.</span></span> <span data-ttu-id="2ce4f-111">Można skojarzyć z pliku Pomocy <xref:System.Windows.Forms.HelpProvider> za pomocą składnika <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-111">You can associate a Help file with the <xref:System.Windows.Forms.HelpProvider> component using the <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property.</span></span> <span data-ttu-id="2ce4f-112">Należy określić typ pomocy udostępniane przez wywołanie metody <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> i podając wartość z zakresu od <xref:System.Windows.Forms.HelpNavigator> wyliczenie dla określonego formantu.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-112">You specify the type of Help provided by calling <xref:System.Windows.Forms.HelpProvider.SetHelpNavigator%2A> and providing a value from the <xref:System.Windows.Forms.HelpNavigator> enumeration for the specified control.</span></span> <span data-ttu-id="2ce4f-113">Podasz — słowo kluczowe lub tematu pomocy, wywołując <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-113">You provide the keyword or topic for Help by calling the <xref:System.Windows.Forms.HelpProvider.SetHelpKeyword%2A> method.</span></span>  
  
 <span data-ttu-id="2ce4f-114">Opcjonalnie, aby skojarzyć określony ciąg pomocy z inną kontrolką, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-114">Optionally, to associate a specific Help string with another control, use the <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> method.</span></span> <span data-ttu-id="2ce4f-115">Ciąg, który należy powiązać z kontrolki przy użyciu tej metody jest wyświetlany w oknie podręcznym, gdy użytkownik naciśnie klawisz F1, gdy kontrolka jest ustawiony fokus.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-115">The string that you associate with a control using this method is displayed in a pop-up window when the user presses the F1 key while the control has focus.</span></span>  
  
 <span data-ttu-id="2ce4f-116">Jeśli <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> nie został ustawiony, należy użyć <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> zapewnienie tekst pomocy.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-116">If <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> has not been set, you must use <xref:System.Windows.Forms.HelpProvider.SetHelpString%2A> to provide the Help text.</span></span> <span data-ttu-id="2ce4f-117">Jeśli ustawisz zarówno <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> i ciąg pomocy na podstawie pomocy <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> mają wyższy priorytet.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-117">If you have set both <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> and the Help string, Help based on <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> will take precedence.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2ce4f-118">Mogą wystąpić problemy przy użyciu ścieżki względnej, określając ścieżkę do pliku pomocy w <xref:System.Windows.Forms.Help.ShowHelp%2A> metody lub <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> właściwość <xref:System.Windows.Forms.HelpProvider> kontroli.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-118">You may encounter problems using the relative path when specifying the path to the Help file in the <xref:System.Windows.Forms.Help.ShowHelp%2A> method or <xref:System.Windows.Forms.HelpProvider.HelpNamespace%2A> property of the <xref:System.Windows.Forms.HelpProvider> control.</span></span> <span data-ttu-id="2ce4f-119">Jako takie Pamiętaj określić plik pomocy za pomocą ścieżki bezwzględnej.</span><span class="sxs-lookup"><span data-stu-id="2ce4f-119">As such, be sure to use the absolute file path to specify the Help file.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ce4f-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2ce4f-120">See also</span></span>

- [<span data-ttu-id="2ce4f-121">Systemy Pomocy w aplikacjach Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2ce4f-121">Help Systems in Windows Forms Applications</span></span>](../advanced/help-systems-in-windows-forms-applications.md)
