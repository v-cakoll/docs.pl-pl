---
title: Dostosuj Dodawanie elementów za pomocą składnika BindingSource
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], creating new items
- BindingSource component [Windows Forms], customizing item addition with
- examples [Windows Forms], BindingSource component
- BindingSource component [Windows Forms], examples
ms.assetid: 1aae11fc-6fb2-4cb9-b3d0-e0638fe77ef0
ms.openlocfilehash: 7d74fe6b4bbb1ddb94b359f5ba3ae32ed398d1dd
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738320"
---
# <a name="how-to-customize-item-addition-with-the-windows-forms-bindingsource"></a><span data-ttu-id="679fe-102">Porady: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="679fe-102">How to: Customize Item Addition with the Windows Forms BindingSource</span></span>
<span data-ttu-id="679fe-103">Gdy używasz składnika <xref:System.Windows.Forms.BindingSource>, aby powiązać formant Windows Forms ze źródłem danych, może się okazać, że konieczne jest dostosowanie tworzenia nowych elementów.</span><span class="sxs-lookup"><span data-stu-id="679fe-103">When you use a <xref:System.Windows.Forms.BindingSource> component to bind a Windows Forms control to a data source, you may find it necessary to customize the creation of new items.</span></span> <span data-ttu-id="679fe-104">Składnik <xref:System.Windows.Forms.BindingSource> ułatwia to poprzez dostarczenie zdarzenia <xref:System.Windows.Forms.BindingSource.AddingNew>, które jest zwykle wywoływane, gdy kontrolka związana wymaga utworzenia nowego elementu.</span><span class="sxs-lookup"><span data-stu-id="679fe-104">The <xref:System.Windows.Forms.BindingSource> component makes this straightforward by providing the <xref:System.Windows.Forms.BindingSource.AddingNew> event, which is typically raised when the bound control needs to create a new item.</span></span> <span data-ttu-id="679fe-105">Program obsługi zdarzeń może zapewnić, że wymagane jest zachowanie niestandardowe (na przykład wywołanie metody w usłudze sieci Web lub pobranie nowego obiektu z fabryki klas).</span><span class="sxs-lookup"><span data-stu-id="679fe-105">Your event handler can provide whatever custom behavior is required (for example, calling a method on a Web service or getting a new object from a class factory).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="679fe-106">Gdy element zostanie dodany przez obsługę zdarzenia <xref:System.Windows.Forms.BindingSource.AddingNew>, Dodawanie nie może być anulowane.</span><span class="sxs-lookup"><span data-stu-id="679fe-106">When an item is added by handling the <xref:System.Windows.Forms.BindingSource.AddingNew> event, the addition cannot be canceled.</span></span>  
  
## <a name="example"></a><span data-ttu-id="679fe-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="679fe-107">Example</span></span>  
 <span data-ttu-id="679fe-108">W poniższym przykładzie pokazano, jak powiązać formant <xref:System.Windows.Forms.DataGridView> z fabryką klas przy użyciu składnika <xref:System.Windows.Forms.BindingSource>.</span><span class="sxs-lookup"><span data-stu-id="679fe-108">The following example demonstrates how to bind a <xref:System.Windows.Forms.DataGridView> control to a class factory by using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="679fe-109">Gdy użytkownik kliknie nowy wiersz kontrolki <xref:System.Windows.Forms.DataGridView>, zdarzenie <xref:System.Windows.Forms.BindingSource.AddingNew> zostanie zgłoszone.</span><span class="sxs-lookup"><span data-stu-id="679fe-109">When the user clicks the <xref:System.Windows.Forms.DataGridView> control's new row, the <xref:System.Windows.Forms.BindingSource.AddingNew> event is raised.</span></span> <span data-ttu-id="679fe-110">Program obsługi zdarzeń tworzy nowy obiekt `DemoCustomer`, który jest przypisany do właściwości <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="679fe-110">The event handler creates a new `DemoCustomer` object, which is assigned to the <xref:System.ComponentModel.AddingNewEventArgs.NewObject%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="679fe-111">Powoduje to dodanie nowego obiektu `DemoCustomer` do listy składników <xref:System.Windows.Forms.BindingSource> i zostanie wyświetlony w nowym wierszu kontrolki <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="679fe-111">This causes the new `DemoCustomer` object to be added to the <xref:System.Windows.Forms.BindingSource> component's list and to be displayed in the new row of the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 [!code-cpp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CPP/form1.cpp#1)]
 [!code-csharp[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/CS/form1.cs#1)]
 [!code-vb[System.Windows.Forms.DataConnector.AddingNew#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnector.AddingNew/VB/form1.vb#1)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="679fe-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="679fe-112">Compiling the Code</span></span>  
 <span data-ttu-id="679fe-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="679fe-113">This example requires:</span></span>  
  
- <span data-ttu-id="679fe-114">Odwołania do zestawów system, system. Data, system. Drawing i system. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="679fe-114">References to the System, System.Data, System.Drawing and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="679fe-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="679fe-115">See also</span></span>

- <xref:System.Windows.Forms.BindingNavigator>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.BindingSource>
- [<span data-ttu-id="679fe-116">BindingSource, składnik</span><span class="sxs-lookup"><span data-stu-id="679fe-116">BindingSource Component</span></span>](bindingsource-component.md)
- [<span data-ttu-id="679fe-117">Instrukcje: powiązanie kontrolki Windows Forms z typem</span><span class="sxs-lookup"><span data-stu-id="679fe-117">How to: Bind a Windows Forms Control to a Type</span></span>](how-to-bind-a-windows-forms-control-to-a-type.md)
