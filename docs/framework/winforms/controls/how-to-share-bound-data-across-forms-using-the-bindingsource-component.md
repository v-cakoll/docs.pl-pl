---
title: 'Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956071"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a><span data-ttu-id="c2c4b-102">Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource</span><span class="sxs-lookup"><span data-stu-id="c2c4b-102">How to: Share Bound Data Across Forms Using the BindingSource Component</span></span>
<span data-ttu-id="c2c4b-103">Możesz łatwo udostępniać dane między formularzami przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-103">You can easily share data across forms using the <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="c2c4b-104">Na przykład możesz chcieć wyświetlić jeden formularz tylko do odczytu, który podsumowuje dane źródła danych i inny formularz edytowalny, który zawiera szczegółowe informacje dotyczące aktualnie wybranego elementu w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-104">For example, you may want to display one read-only form that summarizes the data-source data and another editable form that contains detailed information about the currently selected item in the data source.</span></span> <span data-ttu-id="c2c4b-105">Ten przykład ilustruje ten scenariusz.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-105">This example demonstrates this scenario.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2c4b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="c2c4b-106">Example</span></span>  
 <span data-ttu-id="c2c4b-107">Poniższy przykład kodu demonstruje <xref:System.Windows.Forms.BindingSource> , jak udostępniać dane i powiązane z nią powiązania w formularzach.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-107">The following code example demonstrates how to share a <xref:System.Windows.Forms.BindingSource> and its bound data across forms.</span></span> <span data-ttu-id="c2c4b-108">W tym przykładzie udostępniony <xref:System.Windows.Forms.BindingSource> jest przesyłany do konstruktora formularza podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-108">In this example, the shared <xref:System.Windows.Forms.BindingSource> is passed to the constructor of the child form.</span></span> <span data-ttu-id="c2c4b-109">Formularz podrzędny umożliwia użytkownikowi edytowanie danych dla aktualnie wybranego elementu w formularzu głównym.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-109">The child form allows the user to edit the data for the currently selected item in the main form.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c2c4b-110"><xref:System.Windows.Forms.BindingSource.BindingComplete> Zdarzenie<xref:System.Windows.Forms.BindingSource> dla składnika jest obsługiwane w przykładzie, aby upewnić się, że dwa formularze pozostają zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-110">The <xref:System.Windows.Forms.BindingSource.BindingComplete> event for the <xref:System.Windows.Forms.BindingSource> component is handled in the example to ensure that the two forms remain synchronized.</span></span> <span data-ttu-id="c2c4b-111">Aby uzyskać więcej informacji na temat tego, jak to [zrobić, zobacz How to: Upewnij się, że wiele kontrolek powiązanych z tym samym](../multiple-controls-bound-to-data-source-synchronized.md)źródłem danych pozostanie zsynchronizowane.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-111">For more information about why this is done, see [How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized](../multiple-controls-bound-to-data-source-synchronized.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2c4b-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c2c4b-112">Compiling the Code</span></span>  
 <span data-ttu-id="c2c4b-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c2c4b-113">This example requires:</span></span>  
  
- <span data-ttu-id="c2c4b-114">Odwołania do zestawów system, system. Windows. Forms, system. Drawing, system. Data i system. XML.</span><span class="sxs-lookup"><span data-stu-id="c2c4b-114">References to the System, System.Windows.Forms, System.Drawing, System.Data, and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2c4b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c2c4b-115">See also</span></span>

- [<span data-ttu-id="c2c4b-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="c2c4b-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c2c4b-117">Wiązanie danych formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c2c4b-117">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)
- [<span data-ttu-id="c2c4b-118">Instrukcje: Obsługa błędów i wyjątków występujących podczas wiązania z danymi</span><span class="sxs-lookup"><span data-stu-id="c2c4b-118">How to: Handle Errors and Exceptions that Occur with Databinding</span></span>](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
