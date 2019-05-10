---
title: OpenFileDialog — Informacje o składniku (Formularze systemu Windows)
ms.date: 03/30/2017
f1_keywords:
- OpenFileDialog
helpviewer_keywords:
- OpenFileDialog component [Windows Forms], about OpenFileDialog
- Open File dialog box [Windows Forms], displaying in Windows Forms
ms.assetid: cd717300-46b6-4f82-8207-b218fa7fa407
ms.openlocfilehash: 24327ded50ac927642e2687b40b1f10de9bdf41e
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211700"
---
# <a name="openfiledialog-component-overview-windows-forms"></a><span data-ttu-id="55a98-102">OpenFileDialog — Informacje o składniku (Formularze systemu Windows)</span><span class="sxs-lookup"><span data-stu-id="55a98-102">OpenFileDialog Component Overview (Windows Forms)</span></span>

<span data-ttu-id="55a98-103">Formularze Windows <xref:System.Windows.Forms.OpenFileDialog> składnik to wstępnie skonfigurowane okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="55a98-103">The Windows Forms <xref:System.Windows.Forms.OpenFileDialog> component is a pre-configured dialog box.</span></span> <span data-ttu-id="55a98-104">Jest to ta sama **Otwórz plik** okno dialogowe ujawnione przez system operacyjny Windows.</span><span class="sxs-lookup"><span data-stu-id="55a98-104">It is the same **Open File** dialog box exposed by the Windows operating system.</span></span> <span data-ttu-id="55a98-105">Dziedziczy <xref:System.Windows.Forms.CommonDialog> klasy.</span><span class="sxs-lookup"><span data-stu-id="55a98-105">It inherits from the <xref:System.Windows.Forms.CommonDialog> class.</span></span>

## <a name="use-this-component"></a><span data-ttu-id="55a98-106">Użyj tego składnika</span><span class="sxs-lookup"><span data-stu-id="55a98-106">Use this component</span></span>

<span data-ttu-id="55a98-107">Na użytek ten składnik w swojej aplikacji z systemem Windows jako proste rozwiązanie Wybieranie pliku audytów Konfigurowanie własnego okno dialogowe.</span><span class="sxs-lookup"><span data-stu-id="55a98-107">Use this component within your Windows-based application as a simple solution for file selection in lieu of configuring your own dialog box.</span></span> <span data-ttu-id="55a98-108">Opierając się na standardowych okien dialogowych Windows, możesz tworzyć aplikacje, w których podstawowych funkcji jest natychmiast dobrze znanym użytkownikom.</span><span class="sxs-lookup"><span data-stu-id="55a98-108">By relying on standard Windows dialog boxes, you create applications whose basic functionality is immediately familiar to users.</span></span> <span data-ttu-id="55a98-109">Należy jednak pamiętać, że w przypadku przy użyciu <xref:System.Windows.Forms.OpenFileDialog> składnik, należy napisać własną logiką otwarcia pliku.</span><span class="sxs-lookup"><span data-stu-id="55a98-109">Be aware, however, that when using the <xref:System.Windows.Forms.OpenFileDialog> component, you must write your own file-opening logic.</span></span>

<span data-ttu-id="55a98-110">Użyj <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> metodę, aby wyświetlić okno dialogowe w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="55a98-110">Use the <xref:System.Windows.Forms.CommonDialog.ShowDialog%2A> method to display the dialog at run time.</span></span> <span data-ttu-id="55a98-111">Możesz umożliwić użytkownikom wybór wielokrotny pliki można otworzyć za pomocą <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="55a98-111">You can enable users to multi-select files to be opened with the <xref:System.Windows.Forms.OpenFileDialog.Multiselect%2A> property.</span></span> <span data-ttu-id="55a98-112">Ponadto można użyć <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> właściwości w celu określenia, jeśli pole wyboru tylko do odczytu, pojawi się w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="55a98-112">Additionally, you can use the <xref:System.Windows.Forms.OpenFileDialog.ShowReadOnly%2A> property to determine if a read-only check box appears in the dialog box.</span></span> <span data-ttu-id="55a98-113"><xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> Właściwość wskazuje, czy zaznaczono pole wyboru tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="55a98-113">The <xref:System.Windows.Forms.OpenFileDialog.ReadOnlyChecked%2A> property indicates whether the read-only check box is selected.</span></span> <span data-ttu-id="55a98-114">Na koniec <xref:System.Windows.Forms.FileDialog.Filter%2A> właściwość ustawia bieżący ciągu nazwy pliku filtru, który określa opcje, które są wyświetlane w polu "Typy plików" w oknie dialogowym.</span><span class="sxs-lookup"><span data-stu-id="55a98-114">Finally, the <xref:System.Windows.Forms.FileDialog.Filter%2A> property sets the current file name filter string, which determines the choices that appear in the "Files of type" box in the dialog box.</span></span>

<span data-ttu-id="55a98-115">Gdy zostanie dodany do formularza, <xref:System.Windows.Forms.OpenFileDialog> składnika, który pojawia się na pasku w dolnej części projektanta Windows Forms w programie Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="55a98-115">When it is added to a form, the <xref:System.Windows.Forms.OpenFileDialog> component appears in the tray at the bottom of the Windows Forms Designer in Visual Studio.</span></span>

## <a name="see-also"></a><span data-ttu-id="55a98-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="55a98-116">See also</span></span>

- <xref:System.Windows.Forms.OpenFileDialog>
- [<span data-ttu-id="55a98-117">OpenFileDialog, składnik</span><span class="sxs-lookup"><span data-stu-id="55a98-117">OpenFileDialog Component</span></span>](openfiledialog-component-windows-forms.md)
