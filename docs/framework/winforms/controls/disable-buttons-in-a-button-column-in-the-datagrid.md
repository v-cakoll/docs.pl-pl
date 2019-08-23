---
title: 'Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], disabling buttons
- buttons [Windows Forms], disabling in button columns
- DataGridView control [Windows Forms], disabling button cells
ms.assetid: 5c344d01-013a-4a6b-8f8d-62ec9321d81e
ms.openlocfilehash: b8bb503186e41c682b0685e4c9c4bf0bb3adcbe8
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967397"
---
# <a name="how-to-disable-buttons-in-a-button-column-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="e088c-102">Instrukcje: wyłączanie przycisków w kolumnie przycisków w kontrolce DataGridView formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="e088c-102">How to: Disable Buttons in a Button Column in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="e088c-103"><xref:System.Windows.Forms.DataGridView> Formant<xref:System.Windows.Forms.DataGridViewButtonCell> zawiera klasę służącą do wyświetlania komórek z interfejsem użytkownika (UI), takim jak przycisk.</span><span class="sxs-lookup"><span data-stu-id="e088c-103">The <xref:System.Windows.Forms.DataGridView> control includes the <xref:System.Windows.Forms.DataGridViewButtonCell> class for displaying cells with a user interface (UI) like a button.</span></span> <span data-ttu-id="e088c-104">Jednak program <xref:System.Windows.Forms.DataGridViewButtonCell> nie umożliwia wyłączenia wyglądu przycisku wyświetlanego w komórce.</span><span class="sxs-lookup"><span data-stu-id="e088c-104">However, <xref:System.Windows.Forms.DataGridViewButtonCell> does not provide a way to disable the appearance of the button displayed by the cell.</span></span>  
  
 <span data-ttu-id="e088c-105">Poniższy przykład kodu demonstruje sposób dostosowywania <xref:System.Windows.Forms.DataGridViewButtonCell> klasy do wyświetlania przycisków, które mogą być wyświetlane jako wyłączone.</span><span class="sxs-lookup"><span data-stu-id="e088c-105">The following code example demonstrates how to customize the <xref:System.Windows.Forms.DataGridViewButtonCell> class to display buttons that can appear disabled.</span></span> <span data-ttu-id="e088c-106">W przykładzie zdefiniowano nowy typ `DataGridViewDisableButtonCell`komórki, który pochodzi od. <xref:System.Windows.Forms.DataGridViewButtonCell></span><span class="sxs-lookup"><span data-stu-id="e088c-106">The example defines a new cell type, `DataGridViewDisableButtonCell`, that derives from <xref:System.Windows.Forms.DataGridViewButtonCell>.</span></span> <span data-ttu-id="e088c-107">Ten typ komórki zawiera nową `Enabled` właściwość, którą można `false` ustawić, aby narysować przycisk wyłączony w komórce.</span><span class="sxs-lookup"><span data-stu-id="e088c-107">This cell type provides a new `Enabled` property that can be set to `false` to draw a disabled button in the cell.</span></span> <span data-ttu-id="e088c-108">W przykładzie zdefiniowano również nowy typ `DataGridViewDisableButtonColumn`kolumny, który wyświetla `DataGridViewDisableButtonCell` obiekty.</span><span class="sxs-lookup"><span data-stu-id="e088c-108">The example also defines a new column type, `DataGridViewDisableButtonColumn`, that displays `DataGridViewDisableButtonCell` objects.</span></span> <span data-ttu-id="e088c-109">Aby pokazać tę nową komórkę i typ kolumny, bieżąca <xref:System.Windows.Forms.DataGridViewCheckBoxCell> wartość każdego w obiekcie nadrzędnym <xref:System.Windows.Forms.DataGridView> określa, `DataGridViewDisableButtonCell` czy `Enabled` właściwość w tym samym wierszu jest `true` lub `false`.</span><span class="sxs-lookup"><span data-stu-id="e088c-109">To demonstrate this new cell and column type, the current value of each <xref:System.Windows.Forms.DataGridViewCheckBoxCell> in the parent <xref:System.Windows.Forms.DataGridView> determines whether the `Enabled` property of the `DataGridViewDisableButtonCell` in the same row is `true` or `false`.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="e088c-110">Gdy pochodzą z <xref:System.Windows.Forms.DataGridViewCell> lub <xref:System.Windows.Forms.DataGridViewColumn> i dodajesz nowe właściwości do klasy pochodnej, pamiętaj, aby zastąpić `Clone` metodę, aby skopiować nowe właściwości podczas klonowania operacji.</span><span class="sxs-lookup"><span data-stu-id="e088c-110">When you derive from <xref:System.Windows.Forms.DataGridViewCell> or <xref:System.Windows.Forms.DataGridViewColumn> and add new properties to the derived class, be sure to override the `Clone` method to copy the new properties during cloning operations.</span></span> <span data-ttu-id="e088c-111">Należy również wywołać `Clone` metodę klasy bazowej, aby właściwości klasy bazowej były kopiowane do nowej komórki lub kolumny.</span><span class="sxs-lookup"><span data-stu-id="e088c-111">You should also call the base class's `Clone` method so that the properties of the base class are copied to the new cell or column.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e088c-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="e088c-112">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.DataGridView.DisabledButtons#0](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.DisabledButtons/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e088c-113">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="e088c-113">Compiling the Code</span></span>  
 <span data-ttu-id="e088c-114">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="e088c-114">This example requires:</span></span>  
  
- <span data-ttu-id="e088c-115">Odwołania do zestawów system, system. Drawing, system. Windows. Forms i system. Windows. Forms. VisualStyles.</span><span class="sxs-lookup"><span data-stu-id="e088c-115">References to the System, System.Drawing, System.Windows.Forms and System.Windows.Forms.VisualStyles assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e088c-116">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e088c-116">See also</span></span>

- [<span data-ttu-id="e088c-117">Dostosowywanie kontrolki DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e088c-117">Customizing the Windows Forms DataGridView Control</span></span>](customizing-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e088c-118">DataGridView, kontrolka — architektura</span><span class="sxs-lookup"><span data-stu-id="e088c-118">DataGridView Control Architecture</span></span>](datagridview-control-architecture-windows-forms.md)
- [<span data-ttu-id="e088c-119">Typy kolumn w kontrolce DataGridView formularzy Windows Forms</span><span class="sxs-lookup"><span data-stu-id="e088c-119">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
