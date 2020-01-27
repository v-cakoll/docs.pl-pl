---
title: Implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w formancie DataGridView
ms.date: 03/30/2017
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
ms.openlocfilehash: bbe98d3c317a7625b36b729f0be23ea20f65dec0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745426"
---
# <a name="how-to-implement-virtual-mode-with-just-in-time-data-loading-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d897e-102">Porady: implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="d897e-102">How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d897e-103">Poniższy przykład kodu pokazuje, jak używać trybu wirtualnego w kontrolce <xref:System.Windows.Forms.DataGridView> z pamięcią podręczną danych, która ładuje dane z serwera tylko wtedy, gdy jest to konieczne.</span><span class="sxs-lookup"><span data-stu-id="d897e-103">The following code example shows how to use virtual mode in the <xref:System.Windows.Forms.DataGridView> control with a data cache that loads data from a server only when it is needed.</span></span> <span data-ttu-id="d897e-104">Ten przykład został szczegółowo opisany w temacie [implementowanie trybu wirtualnego przy użyciu ładowania danych just-in-Time w kontrolce DataGridView Windows Forms](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="d897e-104">This example is described in detail in [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d897e-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="d897e-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/CS/lazyloading.cs#000)]
 [!code-vb[System.Windows.Forms.DataGridView.Virtual_lazyloading#000](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.Virtual_lazyloading/VB/lazyloading.vb#000)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d897e-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="d897e-106">Compiling the Code</span></span>  
 <span data-ttu-id="d897e-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="d897e-107">This example requires:</span></span>  
  
- <span data-ttu-id="d897e-108">Odwołania do zestawów system, system. Data, system. XML i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="d897e-108">References to the System, System.Data, System.Xml, and System.Windows.Forms assemblies.</span></span>  
  
- <span data-ttu-id="d897e-109">Dostęp do serwera z zainstalowaną przykładową bazą danych Northwind SQL Server.</span><span class="sxs-lookup"><span data-stu-id="d897e-109">Access to a server with the Northwind SQL Server sample database installed.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="d897e-110">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d897e-110">.NET Framework Security</span></span>  
 <span data-ttu-id="d897e-111">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="d897e-111">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="d897e-112">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="d897e-112">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="d897e-113">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="d897e-113">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d897e-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d897e-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>
- <xref:System.Windows.Forms.DataGridView.CellValueNeeded>
- [<span data-ttu-id="d897e-115">Implementowanie trybu wirtualnego przy użyciu ładowania danych Just-In-Time w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d897e-115">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)
- [<span data-ttu-id="d897e-116">Dostrajanie wydajności w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d897e-116">Performance Tuning in the Windows Forms DataGridView Control</span></span>](performance-tuning-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="d897e-117">Tryb wirtualny w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d897e-117">Virtual Mode in the Windows Forms DataGridView Control</span></span>](virtual-mode-in-the-windows-forms-datagridview-control.md)
