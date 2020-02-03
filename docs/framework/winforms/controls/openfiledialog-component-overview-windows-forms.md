---
title: OpenFileDialog, składnik — omówienie
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: c519b373150a49ee41dbb0c503f7d5a4862477d5
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728440"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="884c6-102">OpenFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="884c6-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="884c6-103">Składnik <xref:System.Windows.Forms.OpenFileDialog> Windows Forms jest wstępnie skonfigurowanym oknem dialogowym.</span><span class="sxs-lookup"><span data-stu-id="884c6-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="884c6-104">Jest to to samo okno dialogowe **Otwórz plik** uwidocznione przez system operacyjny Windows.</span><span class="sxs-lookup"><span data-stu-id="884c6-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="884c6-105">Dziedziczy z klasy <xref:System.Windows.Forms.CommonDialog>.</span><span class="sxs-lookup"><span data-stu-id="884c6-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="884c6-106">Użyj tego składnika</span><span class="sxs-lookup"><span data-stu-id="884c6-106">Use this component</span></span>

<span data-ttu-id="884c6-107">Użyj tego składnika w aplikacji opartej na systemie Windows jako prostego rozwiązania do wyboru plików zamiast konfigurowania własnego okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="884c6-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="884c6-108">Polegając na standardowych oknach dialogowych systemu Windows, można tworzyć aplikacje, których podstawowe funkcje są bezpośrednio znane użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="884c6-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="884c6-109">Należy jednak pamiętać, że w przypadku korzystania ze składnika <xref:System.Windows.Forms.OpenFileDialog> należy napisać własną logikę otwierania plików.</span><span class="sxs-lookup"><span data-stu-id="884c6-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="884c6-110">Użyj metody <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A>, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="884c6-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="884c6-111">Możesz zezwolić użytkownikom na otwieranie plików z możliwością wyboru przy użyciu właściwości <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A>.</span><span class="sxs-lookup"><span data-stu-id="884c6-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="884c6-112">Ponadto można użyć właściwości <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A>, aby określić, czy w oknie dialogowym pojawi się pole wyboru tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="884c6-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="884c6-113">Właściwość <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> wskazuje, czy jest zaznaczone pole wyboru tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="884c6-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="884c6-114">Na koniec Właściwość <xref:System.Windows.Forms.FileDialog.Filter%2A> ustawia bieżący ciąg filtru nazwy pliku, który określa opcje, które pojawiają się w polu "Pliki typu" w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="884c6-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="884c6-115">Po dodaniu do formularza składnik <xref:System.Windows.Forms.OpenFileDialog> pojawia się w zasobniku u dołu Projektant formularzy systemu Windows w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="884c6-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="884c6-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="884c6-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="884c6-117">OpenFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="884c6-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
