---
title: 'Instrukcje: ustawienie modułu renderowania ToolStrip w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- toolbars [Windows Forms]
- ToolStripManager class [Windows Forms]
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStrip control [Windows Forms]
- MenuStrip control [Windows Forms]
ms.assetid: 525e2347-0804-49aa-b9a3-9b2cabbf1c35
ms.openlocfilehash: 90a80ba421698a108cd7a358f89b64810b06efc9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591615"
---
# <a name="how-to-set-the-toolstrip-renderer-at-run-time"></a><span data-ttu-id="77416-102">Instrukcje: ustawienie modułu renderowania ToolStrip w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="77416-102">How to: Set the ToolStrip Renderer at Run Time</span></span>
<span data-ttu-id="77416-103">Można dostosować wygląd Twojego <xref:System.Windows.Forms.ToolStrip> kontroli, tworząc niestandardowe `ProfessionalColorTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="77416-103">You can customize the appearance of your <xref:System.Windows.Forms.ToolStrip> control by creating a custom `ProfessionalColorTable` class.</span></span>  
  
## <a name="example"></a><span data-ttu-id="77416-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="77416-104">Example</span></span>  
 <span data-ttu-id="77416-105">Poniższy przykład kodu pokazuje, jak utworzyć niestandardową `ProfessionalColorTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="77416-105">The following code example demonstrates how to create a custom `ProfessionalColorTable` class.</span></span> <span data-ttu-id="77416-106">Ta klasa definiuje gradientów <xref:System.Windows.Forms.MenuStrip> i <xref:System.Windows.Forms.ToolStrip> kontroli.</span><span class="sxs-lookup"><span data-stu-id="77416-106">This class defines gradients for a <xref:System.Windows.Forms.MenuStrip> and a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
 <span data-ttu-id="77416-107">Aby wykorzystać ten przykład kodu, skompiluj i uruchom aplikację, a następnie kliknij **Zmienianie kolorów** do zastosowania gradientów zdefiniowany w niestandardowej `ProfessionalColorTable` klasy.</span><span class="sxs-lookup"><span data-stu-id="77416-107">To use this code example, compile and run the application, and then click **Change Colors** to apply the gradients defined in the custom `ProfessionalColorTable` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#1)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#1)]  
[!code-csharp[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#20)]
[!code-vb[System.Windows.Forms.ToolStrip.Misc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#20)]  
  
## <a name="defining-a-custom-professionalcolortable-class"></a><span data-ttu-id="77416-108">Definiowanie niestandardowego professionalcolortable — klasa</span><span class="sxs-lookup"><span data-stu-id="77416-108">Defining a Custom ProfessionalColorTable class</span></span>  
 <span data-ttu-id="77416-109">Gradienty niestandardowe są zdefiniowane w `CustomProfessionalColors` klasy.</span><span class="sxs-lookup"><span data-stu-id="77416-109">The custom gradients are defined in the `CustomProfessionalColors` class.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#30)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#30)]  
  
## <a name="assigning-a-custom-renderer"></a><span data-ttu-id="77416-110">Przypisywanie niestandardowego modułu renderowania</span><span class="sxs-lookup"><span data-stu-id="77416-110">Assigning a Custom Renderer</span></span>  
 <span data-ttu-id="77416-111">Utwórz nową `ToolStripProfessionalRenderer` z `CustomProfessionalColors` klasy i przypisz ją do <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> właściwości.</span><span class="sxs-lookup"><span data-stu-id="77416-111">Create a new `ToolStripProfessionalRenderer` with a `CustomProfessionalColors` class, and assign it to the <xref:System.Windows.Forms.ToolStripManager.Renderer%2A?displayProperty=nameWithType> property.</span></span>  
  
 [!code-csharp[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/CS/Program.cs#22)]
 [!code-vb[System.Windows.Forms.ToolStrip.Misc#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.Misc/VB/Program.vb#22)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="77416-112">Kompilowanie kodu</span><span class="sxs-lookup"><span data-stu-id="77416-112">Compiling the Code</span></span>  
 <span data-ttu-id="77416-113">Ten przykład wymaga:</span><span class="sxs-lookup"><span data-stu-id="77416-113">This example requires:</span></span>  
  
- <span data-ttu-id="77416-114">Odwołania do zestawów System.Design System.Drawing i przestrzeń nazw System.Windows.Forms.</span><span class="sxs-lookup"><span data-stu-id="77416-114">References to the System.Design, System.Drawing, and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="77416-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="77416-115">See also</span></span>

- <xref:System.Windows.Forms.ToolStripManager>
- <xref:System.Windows.Forms.ProfessionalColorTable>
- <xref:System.Windows.Forms.MenuStrip>
- <xref:System.Windows.Forms.ToolStrip>
- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>
- [<span data-ttu-id="77416-116">ToolStrip, kontrolka</span><span class="sxs-lookup"><span data-stu-id="77416-116">ToolStrip Control</span></span>](toolstrip-control-windows-forms.md)
