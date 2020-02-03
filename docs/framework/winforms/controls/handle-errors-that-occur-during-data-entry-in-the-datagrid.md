---
title: Obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- error handling [Windows Forms], dataGridView control
- data grids [Windows Forms], error handling
- DataGridView control [Windows Forms], error handling
- data entry [Windows Forms], error handling
- error handling [Windows Forms], data entry
ms.assetid: 9004e72f-fdec-4264-a37d-2c99764efc13
ms.openlocfilehash: 03a13957c80b0ab62afb11efc57cf31e059e5942
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745614"
---
# <a name="how-to-handle-errors-that-occur-during-data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="be39f-102">Porady: obsługa błędów występujących podczas wprowadzania danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="be39f-102">How to: Handle Errors That Occur During Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="be39f-103">Poniższy przykład kodu ilustruje sposób używania kontrolki <xref:System.Windows.Forms.DataGridView> do raportowania błędów wprowadzania danych do użytkownika.</span><span class="sxs-lookup"><span data-stu-id="be39f-103">The following code example demonstrates how to use the <xref:System.Windows.Forms.DataGridView> control to report data entry errors to the user.</span></span>  
  
 <span data-ttu-id="be39f-104">Aby uzyskać kompletny opis tego przykładu kodu, zobacz [Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView Windows Forms](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span><span class="sxs-lookup"><span data-stu-id="be39f-104">For a complete explanation of this code example, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="be39f-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="be39f-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/CS/errorhandling.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.DataError#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DataError/VB/errorhandling.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="be39f-106">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="be39f-106">Compiling the Code</span></span>  
 <span data-ttu-id="be39f-107">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="be39f-107">This example requires:</span></span>  
  
- <span data-ttu-id="be39f-108">Odwołania do zestawów system, system. Data, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="be39f-108">References to the System, System.Data, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="be39f-109">Zabezpieczenia.NET Framework</span><span class="sxs-lookup"><span data-stu-id="be39f-109">.NET Framework Security</span></span>  
 <span data-ttu-id="be39f-110">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="be39f-110">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="be39f-111">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="be39f-111">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="be39f-112">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="be39f-112">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="be39f-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="be39f-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="be39f-114">Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be39f-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="be39f-115">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be39f-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="be39f-116">Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="be39f-116">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="be39f-117">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="be39f-117">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
