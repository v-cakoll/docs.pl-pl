---
title: Sprawdzanie poprawności danych w formancie DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data [Windows Forms], validation
- DataGridView control [Windows Forms], data validation
- data grids [Windows Forms], validating data
- data validation [Windows Forms], Windows Forms
ms.assetid: d10aef35-701e-4a3c-a684-2a2ed1aeaca6
ms.openlocfilehash: 5fd881829f87fa1dec135d936f22996f196b0594
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728309"
---
# <a name="how-to-validate-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="653eb-102">Porady: sprawdzanie poprawności danych w formancie DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="653eb-102">How to: Validate Data in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="653eb-103">Poniższy przykład kodu demonstruje, jak sprawdzać poprawność danych wprowadzonych przez użytkownika w kontrolce <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="653eb-103">The following code example demonstrates how to validate data entered by a user into a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="653eb-104">W tym przykładzie <xref:System.Windows.Forms.DataGridView> jest wypełniany wierszami z tabeli `Customers` przykładowej bazy danych Northwind.</span><span class="sxs-lookup"><span data-stu-id="653eb-104">In this example, the <xref:System.Windows.Forms.DataGridView> is populated with rows from the `Customers` table of the Northwind sample database.</span></span> <span data-ttu-id="653eb-105">Gdy użytkownik edytuje komórkę w `CompanyName` kolumnie, jej wartość jest testowana pod kątem ważności, sprawdzając, czy nie jest pusta.</span><span class="sxs-lookup"><span data-stu-id="653eb-105">When the user edits a cell in the `CompanyName` column, its value is tested for validity by checking that it is not empty.</span></span> <span data-ttu-id="653eb-106">Jeśli program obsługi zdarzeń dla zdarzenia <xref:System.Windows.Forms.DataGridView.CellValidating> stwierdzi, że wartość jest pustym ciągiem, <xref:System.Windows.Forms.DataGridView> uniemożliwia użytkownikowi opuszczenie komórki do momentu wprowadzenia niepustego ciągu.</span><span class="sxs-lookup"><span data-stu-id="653eb-106">If the event handler for the <xref:System.Windows.Forms.DataGridView.CellValidating> event finds that the value is an empty string, the <xref:System.Windows.Forms.DataGridView> prevents the user from exiting the cell until a non-empty string is entered.</span></span>  
  
 <span data-ttu-id="653eb-107">Aby uzyskać kompletny opis tego przykładu kodu, zobacz [Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView Windows Forms](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span><span class="sxs-lookup"><span data-stu-id="653eb-107">For a complete explanation of this code example, see [Walkthrough: Validating Data in the Windows Forms DataGridView Control](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="653eb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="653eb-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/CS/datavalidation.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewDataValidation#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewDataValidation/VB/datavalidation.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="653eb-109">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="653eb-109">Compiling the Code</span></span>  
 <span data-ttu-id="653eb-110">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="653eb-110">This example requires:</span></span>  
  
- <span data-ttu-id="653eb-111">Odwołania do zestawów system, system. Data, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="653eb-111">References to the System, System.Data, System.Windows.Forms and System.XML assemblies.</span></span>  
  
## <a name="net-framework-security"></a><span data-ttu-id="653eb-112">Zabezpieczenia programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="653eb-112">.NET Framework Security</span></span>  
 <span data-ttu-id="653eb-113">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="653eb-113">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="653eb-114">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="653eb-114">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="653eb-115">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="653eb-115">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="653eb-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="653eb-116">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="653eb-117">Przewodnik: sprawdzanie poprawności danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653eb-117">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="653eb-118">Wprowadzanie danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653eb-118">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="653eb-119">Przewodnik: obsługa błędów występujących podczas wprowadzania danych w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="653eb-119">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)
- [<span data-ttu-id="653eb-120">Ochrona informacji o połączeniu</span><span class="sxs-lookup"><span data-stu-id="653eb-120">Protecting Connection Information</span></span>](../../data/adonet/protecting-connection-information.md)
