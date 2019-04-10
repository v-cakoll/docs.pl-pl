---
title: 'Instrukcje: Wywoływanie okna dialogowego drukowania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- invoking print dialogs [WPF]
- print dialogs [WPF], invoking
ms.assetid: e3a2c84c-74fe-45a4-8501-5813f9dbfed2
ms.openlocfilehash: 2ced508eb83e2955fdcd1ad87fb6415e2052446f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59206047"
---
# <a name="how-to-invoke-a-print-dialog"></a><span data-ttu-id="e3775-102">Instrukcje: Wywoływanie okna dialogowego drukowania</span><span class="sxs-lookup"><span data-stu-id="e3775-102">How to: Invoke a Print Dialog</span></span>
<span data-ttu-id="e3775-103">Aby zapewnić możliwość drukowania z aplikacji, można po prostu utworzyć i otworzyć <xref:System.Windows.Controls.PrintDialog> obiektu.</span><span class="sxs-lookup"><span data-stu-id="e3775-103">To provide the ability to print from you application, you can simply create and open a <xref:System.Windows.Controls.PrintDialog> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3775-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3775-104">Example</span></span>  
 <span data-ttu-id="e3775-105"><xref:System.Windows.Controls.PrintDialog> Kontrola zapewnia jeden punkt wejścia dla [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], konfiguracji i [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] przesyłania zadania.</span><span class="sxs-lookup"><span data-stu-id="e3775-105">The <xref:System.Windows.Controls.PrintDialog> control provides a single entry point for [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], configuration, and [!INCLUDE[TLA2#tla_metro](../../../../includes/tla2sharptla-metro-md.md)] job submission.</span></span> <span data-ttu-id="e3775-106">Kontrolka jest łatwa w użyciu i mogą być utworzone przy użyciu [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] znaczników lub innego kodu.</span><span class="sxs-lookup"><span data-stu-id="e3775-106">The control is easy to use and can be instantiated by using [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] markup or code.</span></span> <span data-ttu-id="e3775-107">Poniższy przykład pokazuje, jak do tworzenia instancji i otwórz kontrolki w kodzie i jak go wydrukować.</span><span class="sxs-lookup"><span data-stu-id="e3775-107">The following example demonstrates how to instantiate and open the control in code and how to print from it.</span></span> <span data-ttu-id="e3775-108">Pokazano również, jak upewnić się, że okno dialogowe będzie przyznać użytkownikowi możliwość ustawiania określony zakres stron.</span><span class="sxs-lookup"><span data-stu-id="e3775-108">It also shows how to ensure that the dialog will give the user the option of setting a specific range of pages.</span></span> <span data-ttu-id="e3775-109">Przykładowy kod zakłada, że jest plikiem FixedDocumentSequence.xps w folderze głównym dysku C:.</span><span class="sxs-lookup"><span data-stu-id="e3775-109">The example code assumes that there is a file FixedDocumentSequence.xps in the root of the C: drive.</span></span>  
  
 [!code-csharp[printdialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PrintDialog/CSharp/Window1.xaml.cs#1)]
 [!code-vb[printdialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PrintDialog/visualbasic/window1.xaml.vb#1)]  
  
 <span data-ttu-id="e3775-110">Po otwarciu okna dialogowego, użytkownicy będą mogli wybierać drukarek zainstalowanych na komputerze.</span><span class="sxs-lookup"><span data-stu-id="e3775-110">Once the dialog is open, users will be able to select from the printers installed on their computer.</span></span> <span data-ttu-id="e3775-111">Mają również możliwość wyboru [modułu zapisywania dokumentów XPS firmy Microsoft](https://go.microsoft.com/fwlink/?LinkId=147319) utworzyć [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] zamiast drukowania pliku.</span><span class="sxs-lookup"><span data-stu-id="e3775-111">They will also have the option of selecting the [Microsoft XPS Document Writer](https://go.microsoft.com/fwlink/?LinkId=147319) to create an [!INCLUDE[TLA#tla_xps](../../../../includes/tlasharptla-xps-md.md)] file instead of printing.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e3775-112"><xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> Kontrolę nad [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], która została omówiona w tym temacie, nie należy mylić z <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> składnika Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="e3775-112">The <xref:System.Windows.Controls.PrintDialog?displayProperty=nameWithType> control of [!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)], which is discussed in this topic, should not be confused with the <xref:System.Windows.Forms.PrintDialog?displayProperty=nameWithType> component of Windows Forms.</span></span>  
  
 <span data-ttu-id="e3775-113">Ściśle rzecz ujmując, możesz użyć <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> metody bez konieczności otwierania okna dialogowego.</span><span class="sxs-lookup"><span data-stu-id="e3775-113">Strictly speaking, you can use the <xref:System.Windows.Controls.PrintDialog.PrintDocument%2A> method without ever opening the dialog.</span></span> <span data-ttu-id="e3775-114">W tym sensie formant może służyć jako składnika niewidzianych drukowania.</span><span class="sxs-lookup"><span data-stu-id="e3775-114">In that sense, the control can be used as an unseen printing component.</span></span> <span data-ttu-id="e3775-115">Jednak ze względu na wydajność będzie lepiej używać albo <xref:System.Printing.PrintQueue.AddJob%2A> metody lub jednego z wielu <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> i <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> metody <xref:System.Windows.Xps.XpsDocumentWriter>.</span><span class="sxs-lookup"><span data-stu-id="e3775-115">But for performance reasons, it would be better to use either the <xref:System.Printing.PrintQueue.AddJob%2A> method or one of the many <xref:System.Windows.Xps.XpsDocumentWriter.Write%2A> and <xref:System.Windows.Xps.XpsDocumentWriter.WriteAsync%2A> methods of the <xref:System.Windows.Xps.XpsDocumentWriter>.</span></span> <span data-ttu-id="e3775-116">Aby uzyskać więcej informacji na ten temat, zobacz [programowe drukowanie plików XPS](how-to-programmatically-print-xps-files.md) i.</span><span class="sxs-lookup"><span data-stu-id="e3775-116">For more about this, see [Programmatically Print XPS Files](how-to-programmatically-print-xps-files.md) and .</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e3775-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e3775-117">See also</span></span>

- <xref:System.Windows.Controls.PrintDialog>
- [<span data-ttu-id="e3775-118">Dokumenty w WPF</span><span class="sxs-lookup"><span data-stu-id="e3775-118">Documents in WPF</span></span>](documents-in-wpf.md)
- [<span data-ttu-id="e3775-119">Przegląd Drukowanie</span><span class="sxs-lookup"><span data-stu-id="e3775-119">Printing Overview</span></span>](printing-overview.md)
- [<span data-ttu-id="e3775-120">Moduł zapisywania dokumentów XPS firmy Microsoft</span><span class="sxs-lookup"><span data-stu-id="e3775-120">Microsoft XPS Document Writer</span></span>](https://go.microsoft.com/fwlink/?LinkId=147319)
