---
title: 'Porady: implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], just-in-time data loading
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- just-in-time data loading
- DataGridView control [Windows Forms], large data sets
- virtual mode [Windows Forms], just-in-time data loading
ms.assetid: 33825f92-7a22-40ee-86d9-9a2ed1ead7b7
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 69e355fa2ef6c1ae3c287414f932207720e507ff
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="7e3a2-102">Porady: implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="7e3a2-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="7e3a2-103">Poniższy przykładowy kod przedstawia sposób użycia tryb wirtualny w <xref:System.Windows.Forms.DataGridView> kontrolki z pamięci podręcznej danych, który ładuje dane z serwera tylko wtedy, gdy jest to potrzebne.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="7e3a2-104">W tym przykładzie opisano szczegółowo w [Implementowanie trybu wirtualnego przy użyciu just in time w formancie DataGridView formularzy systemu Windows podczas ładowania danych](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="7e3a2-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e3a2-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e3a2-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7e3a2-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="7e3a2-106">Compiling the Code</span></span>  
 <span data-ttu-id="7e3a2-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="7e3a2-107">This example requires:</span></span>  
  
-   <span data-ttu-id="7e3a2-108">Odwołania do zestawów systemu, dane systemowe System.Xml i System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
-   <span data-ttu-id="7e3a2-109">Dostęp do serwera z bazy danych przykładowych Northwind SQL Server, które zostały zainstalowane.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
 <span data-ttu-id="7e3a2-110">Uzyskać informacje o kompilowaniu w tym przykładzie z wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [kompilowania z wiersza polecenia csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="7e3a2-110">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="7e3a2-111">Można także utworzyć tym przykładzie [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] przez wklejenie kodu do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-111">You can also build this example in [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] by pasting the code into a new project.</span></span>  <span data-ttu-id="7e3a2-112">Zobacz też [porady: kompilowanie i uruchamianie pełną Windows formularze kodu przykład za pomocą programu Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="7e3a2-112">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="7e3a2-113">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="7e3a2-113">.NET Framework Security</span></span>  
 <span data-ttu-id="7e3a2-114">Przechowywanie poufne informacje, takie jak hasła, w ciągu połączenia może mieć wpływ na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-114">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="7e3a2-115">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="7e3a2-115">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="7e3a2-116">Aby uzyskać więcej informacji, zobacz [ochrony informacji o połączeniu](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="7e3a2-116">For more information, see [Protecting Connection Information](../../../../docs/framework/data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e3a2-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e3a2-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 [<span data-ttu-id="7e3a2-118">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e3a2-118">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="7e3a2-119">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e3a2-119">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="7e3a2-120">Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e3a2-120">Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/virtual-mode-in-the-windows-forms-datagridview-control.md)
