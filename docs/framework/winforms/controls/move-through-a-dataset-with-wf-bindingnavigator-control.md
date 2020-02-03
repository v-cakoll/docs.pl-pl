---
title: Przechodzenie przez zestaw danych przy użyciu kontrolki BindingNavigator
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: 73a102da74a3a2a00b5042331cffcaf3d858ea5b
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742151"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="1821b-102">Porady: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="1821b-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="1821b-103">Podczas kompilowania aplikacji opartych na danych często konieczne jest wyświetlenie kolekcji danych dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="1821b-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="1821b-104">Kontrolka <xref:System.Windows.Forms.BindingNavigator>, w połączeniu ze składnikiem <xref:System.Windows.Forms.BindingSource>, oferuje wygodne i rozszerzalne rozwiązanie do poruszania się po kolekcji i wyświetlania elementów sekwencyjnie.</span><span class="sxs-lookup"><span data-stu-id="1821b-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1821b-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="1821b-105">Example</span></span>  
 <span data-ttu-id="1821b-106">Poniższy przykład kodu ilustruje sposób używania kontrolki <xref:System.Windows.Forms.BindingNavigator> do przenoszenia danych.</span><span class="sxs-lookup"><span data-stu-id="1821b-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="1821b-107">Zestaw jest zawarty w <xref:System.Data.DataView>, który jest powiązany z kontrolką <xref:System.Windows.Forms.TextBox> ze składnikiem <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="1821b-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="1821b-108">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="1821b-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="1821b-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="1821b-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="1821b-110">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="1821b-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1821b-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="1821b-111">Compiling the Code</span></span>  
 <span data-ttu-id="1821b-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="1821b-112">This example requires:</span></span>  
  
- <span data-ttu-id="1821b-113">Odwołania do zestawów system, system. Data, system. Drawing, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="1821b-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1821b-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1821b-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="1821b-115">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="1821b-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="1821b-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="1821b-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="1821b-117">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="1821b-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
