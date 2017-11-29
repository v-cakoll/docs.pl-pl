---
title: 'Porady: ukrywanie formantu w czasie wykonywania'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 310750df0786eb07158909eb5e322369d157d1cb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="f36ed-102">Porady: ukrywanie formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="f36ed-102">How to: Make Your Control Invisible at Run Time</span></span>
<span data-ttu-id="f36ed-103">Brak godziny, kiedy warto utworzyć kontrolkę użytkownika, która jest niewidoczna w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f36ed-103">There are times when you might want to create a user control that is invisible at run time.</span></span> <span data-ttu-id="f36ed-104">Na przykład formant, który jest zegar alarm może być niewidoczna z wyjątkiem przypadków, gdy został podawania alarm.</span><span class="sxs-lookup"><span data-stu-id="f36ed-104">For example, a control that is an alarm clock might be invisible except when the alarm was sounding.</span></span> <span data-ttu-id="f36ed-105">Łatwo jest to osiągane przez ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości.</span><span class="sxs-lookup"><span data-stu-id="f36ed-105">This is easily accomplished by setting the <xref:System.Windows.Forms.Control.Visible%2A> property.</span></span> <span data-ttu-id="f36ed-106">Jeśli <xref:System.Windows.Forms.Control.Visible%2A> właściwość jest `true`, formantu będą wyświetlane jako standardowa.</span><span class="sxs-lookup"><span data-stu-id="f36ed-106">If the <xref:System.Windows.Forms.Control.Visible%2A> property is `true`, your control will appear as normal.</span></span> <span data-ttu-id="f36ed-107">Jeśli `false`, formantu zostanie ukryta.</span><span class="sxs-lookup"><span data-stu-id="f36ed-107">If `false`, your control will be hidden.</span></span> <span data-ttu-id="f36ed-108">Mimo że kod formantu mogą nadal działać podczas niewidoczne, nie będzie możliwość interakcji z formantem za pomocą interfejsu użytkownika.</span><span class="sxs-lookup"><span data-stu-id="f36ed-108">Although code in your control may still run while invisible, you will not be able to interact with the control through the user interface.</span></span> <span data-ttu-id="f36ed-109">Jeśli chcesz utworzyć niewidocznym formancie nadal odpowiada interakcja z użytkownikiem (na przykład kliknięcie myszą), należy utworzyć przezroczystego formantu.</span><span class="sxs-lookup"><span data-stu-id="f36ed-109">If you want to create an invisible control that still responds to user input (for example, mouse clicks), you should create a transparent control.</span></span> <span data-ttu-id="f36ed-110">Aby uzyskać więcej informacji, zobacz [nadanie przezroczystego tła formantu](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span><span class="sxs-lookup"><span data-stu-id="f36ed-110">For more information, see [Giving Your Control a Transparent Background](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md).</span></span>  
  
### <a name="to-make-your-control-invisible-at-run-time"></a><span data-ttu-id="f36ed-111">Aby ukrywanie formantu w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="f36ed-111">To make your control invisible at run time</span></span>  
  
1.  <span data-ttu-id="f36ed-112">Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwości `false`.</span><span class="sxs-lookup"><span data-stu-id="f36ed-112">Set the <xref:System.Windows.Forms.Control.Visible%2A> property to `false`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f36ed-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f36ed-113">See Also</span></span>  
 <xref:System.Windows.Forms.Control.Visible%2A>  
 [<span data-ttu-id="f36ed-114">Opracowywanie niestandardowych formularzy systemu Windows formantów za pomocą programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="f36ed-114">Developing Custom Windows Forms Controls with the .NET Framework</span></span>](../../../../docs/framework/winforms/controls/developing-custom-windows-forms-controls.md)  
 [<span data-ttu-id="f36ed-115">Porady: zapewniają przezroczystego tła formantu</span><span class="sxs-lookup"><span data-stu-id="f36ed-115">How to: Give Your Control a Transparent Background</span></span>](../../../../docs/framework/winforms/controls/how-to-give-your-control-a-transparent-background.md)
