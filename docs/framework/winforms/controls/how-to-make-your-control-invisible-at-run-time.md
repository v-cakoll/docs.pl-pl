---
title: 'Instrukcje: ukrywanie kontrolki w czasie wykonywania'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [Windows Forms], making invisible at run time
- invisible controls
- user controls [Windows Forms], invisible
- custom controls [Windows Forms], invisible
- run time [Windows Forms], making controls invisible
ms.assetid: 69eb2e72-32f5-4f79-a157-c2c5f60c1628
ms.openlocfilehash: e9af529541a40a951d6defea180dbbef04c8f3be
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61913708"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="d9a34-102">Instrukcje: ukrywanie kontrolki w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="d9a34-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="d9a34-103">Istnieją terminy, gdy możesz chcieć utworzyć formant użytkownika, który jest niewidoczny w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d9a34-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="d9a34-104">Na przykład formant, który jest zegar alarmu, może być niewidoczne, z wyjątkiem sytuacji, kiedy został podawania alarmu.</span><span class="sxs-lookup"><span data-stu-id="d9a34-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="d9a34-105">Łatwo jest to realizowane przez ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="d9a34-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="d9a34-106">Jeśli <xref:System.Windows.Forms.Control.Visible%2A> właściwość `true`, formant pojawi się w zwykły sposób.</span><span class="sxs-lookup"><span data-stu-id="d9a34-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="d9a34-107">Jeśli `false`, kontrolki będą ukryte.</span><span class="sxs-lookup"><span data-stu-id="d9a34-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="d9a34-108">Mimo że kod w kontroli nad może nadal działać podczas niewidoczne, nie można wchodzić w interakcje z kontrolką za pomocą interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="d9a34-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="d9a34-109">Jeśli chcesz utworzyć formant niewidoczne, który nadal odpowiada na dane wejściowe (na przykład kliknięć myszą) użytkownika, należy utworzyć formant przezroczysty.</span><span class="sxs-lookup"><span data-stu-id="d9a34-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="d9a34-110">Aby uzyskać więcej informacji, zobacz [zapewniając ustawienie przezroczystego tła formantu](how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="d9a34-110">For more information, see [Giving Your Control a Transparent Background](how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="d9a34-111">Aby ukrywanie formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="d9a34-111">To make your control invisible at run time</span></span>  
  
1. <span data-ttu-id="d9a34-112">Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwość `false`.</span><span class="sxs-lookup"><span data-stu-id="d9a34-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
    ```vb  
    ' To set the Visible property from within your object's own code.  
    Me.Visible = False  
    ' To set the Visible property from another object.  
    myControl1.Visible = False  
    ```  
  
    ```csharp  
    // To set the Visible property from within your object's own code.  
    this.Visible = false;  
    // To set the Visible property from another object.  
    myControl1.Visible = false;  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="d9a34-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d9a34-113">See also</span></span>

- <xref:System.Windows.Forms.Control.Visible%2A>
- [<span data-ttu-id="d9a34-114">Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="d9a34-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](developing-custom-windows-forms-controls.md)
- [<span data-ttu-id="d9a34-115">Instrukcje: Zachować kontrolę z przezroczystym tłem</span><span class="sxs-lookup"><span data-stu-id="d9a34-115">How to: Give Your Control a Transparent Background</span></span>](how-to-give-your-control-a-transparent-background.md)
