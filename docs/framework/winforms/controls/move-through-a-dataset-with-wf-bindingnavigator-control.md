---
title: 'Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- datasets [Windows Forms], moving through
- BindingNavigator control [Windows Forms], moving through datasets
- examples [Windows Forms], BindingNavigator control
ms.assetid: 146d97be-3d97-400e-accb-860bbf47729d
ms.openlocfilehash: d33cad4d0a60aa29d8c9f5e2217532963e8358c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69952692"
---
# <a name="how-to-move-through-a-dataset-with-the-windows-forms-bindingnavigator-control"></a><span data-ttu-id="c5dd8-102">Instrukcje: przechodzenie między elementami DataSet za pomocą BindingNavigator formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="c5dd8-102">How to: Move Through a DataSet with the Windows Forms BindingNavigator Control</span></span>
<span data-ttu-id="c5dd8-103">Podczas kompilowania aplikacji opartych na danych często konieczne jest wyświetlenie kolekcji danych dla użytkowników.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-103">As you build data-driven applications, you will often need to display collections of data to users.</span></span> <span data-ttu-id="c5dd8-104">Kontrolka, w połączeniu <xref:System.Windows.Forms.BindingSource> z składnikiem, oferuje wygodne i rozszerzalne rozwiązanie do poruszania się po kolekcji i wyświetlania elementów sekwencyjnie. <xref:System.Windows.Forms.BindingNavigator></span><span class="sxs-lookup"><span data-stu-id="c5dd8-104">The <xref:System.Windows.Forms.BindingNavigator> control, in conjunction with the <xref:System.Windows.Forms.BindingSource> component, provides a convenient and extensible solution for moving through a collection and displaying items sequentially.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c5dd8-105">Przykład</span><span class="sxs-lookup"><span data-stu-id="c5dd8-105">Example</span></span>  
 <span data-ttu-id="c5dd8-106">Poniższy przykład kodu demonstruje, jak używać <xref:System.Windows.Forms.BindingNavigator> kontrolki do przenoszenia danych.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-106">The following code example demonstrates how to use a <xref:System.Windows.Forms.BindingNavigator> control to move through data.</span></span> <span data-ttu-id="c5dd8-107">Zestaw jest zawarty w <xref:System.Data.DataView>, który jest powiązany <xref:System.Windows.Forms.TextBox> z kontrolką ze <xref:System.Windows.Forms.BindingSource> składnikiem.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-107">The set is contained in a <xref:System.Data.DataView>, which is bound to a <xref:System.Windows.Forms.TextBox> control with a <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c5dd8-108">Przechowywanie poufnych informacji, takich jak hasło, w ciągu połączenia może wpłynąć na bezpieczeństwo aplikacji.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-108">Storing sensitive information, such as a password, within the connection string can affect the security of your application.</span></span> <span data-ttu-id="c5dd8-109">Korzystanie z uwierzytelniania systemu Windows (znanego również jako zabezpieczenia zintegrowane) jest bezpieczniejszym sposobem na kontrolowanie dostępu do bazy danych.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-109">Using Windows Authentication (also known as integrated security) is a more secure way to control access to a database.</span></span> <span data-ttu-id="c5dd8-110">Aby uzyskać więcej informacji, zobacz [Ochrona informacji o połączeniu](../../data/adonet/protecting-connection-information.md).</span><span class="sxs-lookup"><span data-stu-id="c5dd8-110">For more information, see [Protecting Connection Information](../../data/adonet/protecting-connection-information.md).</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataNavigator#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataNavigator#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataNavigator/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c5dd8-111">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="c5dd8-111">Compiling the Code</span></span>  
 <span data-ttu-id="c5dd8-112">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="c5dd8-112">This example requires:</span></span>  
  
- <span data-ttu-id="c5dd8-113">Odwołania do zestawów system, system. Data, system. Drawing, system. Windows. Forms i system. XML.</span><span class="sxs-lookup"><span data-stu-id="c5dd8-113">References to the System, System.Data, System.Drawing, System.Windows.Forms and System.Xml assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c5dd8-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c5dd8-114">See also</span></span>

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="c5dd8-115">BindingNavigator, kontrolka</span><span class="sxs-lookup"><span data-stu-id="c5dd8-115">BindingNavigator Control</span></span>](bindingnavigator-control-windows-forms.md)
- [<span data-ttu-id="c5dd8-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="c5dd8-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="c5dd8-117">Instrukcje: Powiąż formant Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="c5dd8-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
