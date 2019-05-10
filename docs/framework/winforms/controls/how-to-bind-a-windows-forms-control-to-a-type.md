---
title: 'Instrukcje: powiązanie kontrolki formularzy systemu Windows z typem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], binding to a type
- BindingSource component [Windows Forms], binding to a type
- types [Windows Forms], binding controls to
ms.assetid: 94faeebb-d2bc-45d6-86d7-96a42661b43d
ms.openlocfilehash: 93cf9844a1c5b9d6eb052c94c2309cbff1f4ad56
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64612387"
---
# <a name="how-to-bind-a-windows-forms-control-to-a-type"></a><span data-ttu-id="0fcbd-102">Instrukcje: powiązanie kontrolki formularzy systemu Windows z typem</span><span class="sxs-lookup"><span data-stu-id="0fcbd-102">How to: Bind a Windows Forms Control to a Type</span></span>
<span data-ttu-id="0fcbd-103">Podczas tworzenia formantów, które współdziałają z danymi będą czasami jest konieczne do wiązania kontrolki typu, a nie obiekt.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-103">When you are building controls that interact with data, you will sometimes find it necessary to bind a control to a type, rather than an object.</span></span> <span data-ttu-id="0fcbd-104">Sytuacja ta pojawia się szczególnie w czasie projektowania, gdy dane nie mogą być dostępne, ale formantów powiązanych z danymi potrzebują do wyświetlania informacji z interfejsu publicznego typu.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-104">This situation arises especially at design time, when data may not be available, but your data-bound controls still need to display information from a type's public interface.</span></span> <span data-ttu-id="0fcbd-105">Na przykład może związać <xref:System.Windows.Forms.DataGridView> sterowania do obiektu udostępnianych przez usługi sieci Web i chcesz <xref:System.Windows.Forms.DataGridView> kontrolki etykiety kolumn w czasie projektowania z elementem członkowskim nazwy typu niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-105">For example, you may bind a <xref:System.Windows.Forms.DataGridView> control to an object exposed by a Web service and want the <xref:System.Windows.Forms.DataGridView> control to label its columns at design time with the member names of a custom type.</span></span>  
  
 <span data-ttu-id="0fcbd-106">Można łatwo powiązać formant do typu z <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-106">You can easily bind a control to a type with the <xref:System.Windows.Forms.BindingSource> component.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0fcbd-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="0fcbd-107">Example</span></span>  
 <span data-ttu-id="0fcbd-108">Poniższy przykład kodu pokazuje, jak powiązać <xref:System.Windows.Forms.DataGridView> kontrolki typu niestandardowego za pomocą <xref:System.Windows.Forms.BindingSource> składnika.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-108">The following code example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a custom type by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="0fcbd-109">Po uruchomieniu tego przykładu, można zauważyć <xref:System.Windows.Forms.DataGridView> etykietą kolumn, które odzwierciedlają właściwości `Customer` obiektu, zanim kontrolka jest wypełniana danymi.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-109">When you run the example, you'll notice the <xref:System.Windows.Forms.DataGridView> has labeled columns that reflect the properties of a `Customer` object, before the control is populated with data.</span></span> <span data-ttu-id="0fcbd-110">W przykładzie przedstawiono przycisk Dodaj klienta, aby dodać dane do <xref:System.Windows.Forms.DataGridView> kontroli.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-110">The example has an Add Customer button to add data to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="0fcbd-111">Po kliknięciu przycisku Nowy `Customer` obiekt jest dodawany do <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-111">When you click the button, a new `Customer` object is added to the <xref:System.Windows.Forms.BindingSource>.</span></span> <span data-ttu-id="0fcbd-112">W rzeczywistych scenariuszy dane mogą uzyskać przez wywołanie usługi sieci Web lub innego źródła danych.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-112">In a real-world scenario, the data might be obtained by a call to a Web service or other data source.</span></span>  
  
 [!code-csharp[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.BindingToType#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.BindingToType/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="0fcbd-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="0fcbd-113">Compiling the Code</span></span>  
 <span data-ttu-id="0fcbd-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="0fcbd-114">This example requires:</span></span>  
  
- <span data-ttu-id="0fcbd-115">Odwołania do zestawów System i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-115">References to the System and System.Windows.Forms assemblies.</span></span>  
  
 <span data-ttu-id="0fcbd-116">Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span><span class="sxs-lookup"><span data-stu-id="0fcbd-116">For information about building this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="0fcbd-117">Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.</span><span class="sxs-lookup"><span data-stu-id="0fcbd-117">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0fcbd-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0fcbd-118">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="0fcbd-119">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="0fcbd-119">BindingSource Component</span></span>](bindingsource-component.md)
