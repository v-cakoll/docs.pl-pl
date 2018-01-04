---
title: "OpenFileDialog — Informacje o składniku (Formularze systemu Windows)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3e5dc6630d9bc7a2090a28daabbf08eeed59005
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="878e1-102">OpenFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="878e1-102">OpenFileDialog Component Overview (Windows Forms)</span></span>
<span data-ttu-id="878e1-103">Formularze systemu Windows <xref:System.Windows.Forms.OpenFileDialog> składnik jest okno dialogowe wstępnie skonfigurowane.</span><span class="sxs-lookup"><span data-stu-id="878e1-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="878e1-104">Jest to ten sam **Otwórz plik** okno dialogowe udostępnianych przez system operacyjny Windows.</span><span class="sxs-lookup"><span data-stu-id="878e1-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="878e1-105">Dziedziczy on z <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="878e1-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>  
  
## <a name="using-this-component"></a><span data-ttu-id="878e1-106">Przy użyciu tego składnika</span><span class="sxs-lookup"><span data-stu-id="878e1-106">Using this Component</span></span>  
 <span data-ttu-id="878e1-107">Użyj tego składnika w aplikacji opartych na systemie Windows jako prostym rozwiązaniem dla wyboru plików zamiast własne okno dialogowe Konfigurowanie.</span><span class="sxs-lookup"><span data-stu-id="878e1-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="878e1-108">Polegając na standardowe okno dialogowe systemu Windows, możesz utworzyć aplikacje, których podstawowych funkcji jest znane użytkowników.</span><span class="sxs-lookup"><span data-stu-id="878e1-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="878e1-109">Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.OpenFileDialog> składnika, należy napisać logiki otwierania pliku.</span><span class="sxs-lookup"><span data-stu-id="878e1-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>  
  
 <span data-ttu-id="878e1-110">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę w celu wyświetlenia okna dialogowego w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="878e1-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="878e1-111">Można umożliwić użytkownikom wybrać wiele plików do otwarcia z <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="878e1-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="878e1-112">Ponadto można użyć <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> właściwości w celu określenia, czy pola wyboru tylko do odczytu jest wyświetlany w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="878e1-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="878e1-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Właściwość wskazuje, czy zaznaczone jest pole wyboru tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="878e1-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="878e1-114">Na koniec <xref:System.Windows.Forms.FileDialog.Filter%2A> właściwość ustawia bieżącego pliku nazwę ciąg filtru, który określa opcje, które są wyświetlane w polu "Pliki typu" w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="878e1-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>  
  
 <span data-ttu-id="878e1-115">Gdy jest ona dodawana do formularza, <xref:System.Windows.Forms.OpenFileDialog> składnika jest wyświetlana na pasku w dolnej części Projektant formularzy systemu Windows.</span><span class="sxs-lookup"><span data-stu-id="878e1-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="878e1-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="878e1-116">See Also</span></span>  
 <xref:System.Windows.Forms.OpenFileDialog>  
 [<span data-ttu-id="878e1-117">OpenFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="878e1-117">OpenFileDialog Component</span></span>](../../../../docs/framework/winforms/controls/openfiledialog-component-windows-forms.md)
