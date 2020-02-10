---
title: Jak wywołać okno dialogowe drukowania
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: f7ef3312d876324b44b055d70fd22e3fba075ec6
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/09/2020
ms.locfileid: "77095180"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="6ce64-102">Jak wywołać okno dialogowe drukowania</span><span class="sxs-lookup"><span data-stu-id="6ce64-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="6ce64-103">Aby umożliwić drukowanie z poziomu aplikacji, można po prostu utworzyć i otworzyć obiekt <xref:System.Windows.Controls.PrintDialog>.</span><span class="sxs-lookup"><span data-stu-id="6ce64-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ce64-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ce64-104">Example</span></span>  
 <span data-ttu-id="6ce64-105">Kontrolka <xref:System.Windows.Controls.PrintDialog> zawiera pojedynczy punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i przekazanie zadania XPS.</span><span class="sxs-lookup"><span data-stu-id="6ce64-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and XPS job submission.</span></span> <span data-ttu-id="6ce64-106">Kontrolka jest łatwa w użyciu i można ją utworzyć przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników lub kodu.</span><span class="sxs-lookup"><span data-stu-id="6ce64-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="6ce64-107">W poniższym przykładzie pokazano, jak utworzyć wystąpienie i otworzyć formant w kodzie oraz jak drukować z niego.</span><span class="sxs-lookup"><span data-stu-id="6ce64-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="6ce64-108">Przedstawiono w nim również, jak upewnić się, że w oknie dialogowym zostanie wyświetlona opcja ustawienia określonego zakresu stron.</span><span class="sxs-lookup"><span data-stu-id="6ce64-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="6ce64-109">Przykładowy kod założono, że w katalogu głównym dysku C: znajduje się plik FixedDocumentSequence. XPS.</span><span class="sxs-lookup"><span data-stu-id="6ce64-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="6ce64-110">Po otwarciu okna dialogowego użytkownicy będą mogli wybierać spośród drukarek zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="6ce64-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="6ce64-111">Będą również mieć możliwość wyboru [składnika zapisywania dokumentów XPS firmy Microsoft](/windows/win32/printdocs/microsoft-xps-document-writer) w celu utworzenia pliku specyfikacji XML Paper Specification (XPS) zamiast drukowania.</span><span class="sxs-lookup"><span data-stu-id="6ce64-111">They will also have the option of selecting the [Microsoft XPS Document Writer](/windows/win32/printdocs/microsoft-xps-document-writer) to create an XML Paper Specification (XPS) file instead of printing.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="6ce64-112">Formant <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> WPF, który został omówiony w tym temacie, nie należy mylić ze składnikiem <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="6ce64-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of WPF, which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="6ce64-113">Dokładnie mówiąc, można użyć metody <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> bez konieczności otwierania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="6ce64-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="6ce64-114">W tym sensie formant może być używany jako niewidoczny składnik drukowania.</span><span class="sxs-lookup"><span data-stu-id="6ce64-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="6ce64-115">Jednak ze względu na wydajność lepszym rozwiązaniem jest użycie metody <xref:System.Printing.PrintQueue.AddJob%2A> lub jednej z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metod <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="6ce64-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="6ce64-116">Aby uzyskać więcej informacji na ten temat, zobacz programowe [Drukowanie plików XPS](how-to-programmatically-print-xps-files.md) i.</span><span class="sxs-lookup"><span data-stu-id="6ce64-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ce64-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ce64-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="6ce64-118">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="6ce64-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="6ce64-119">Przegląd drukowania</span><span class="sxs-lookup"><span data-stu-id="6ce64-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="6ce64-120">Moduł zapisywania dokumentów XPS firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="6ce64-120">Microsoft XPS Document Writer</span></span>](/windows/win32/printdocs/microsoft-xps-document-writer)
