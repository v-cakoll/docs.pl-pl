---
title: 'Instrukcje: Ukrywanie formantu w czasie wykonywania'
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
ms.openlocfilehash: 52ea2336bac1ec483cb86e24114090a1b3725038
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57708980"
---
# <a name="how-to-make-your-control-invisible-at-run-time"></a>Instrukcje: Ukrywanie formantu w czasie wykonywania
Istnieją terminy, gdy możesz chcieć utworzyć formant użytkownika, który jest niewidoczny w czasie wykonywania. Na przykład formant, który jest zegar alarmu, może być niewidoczne, z wyjątkiem sytuacji, kiedy został podawania alarmu. Łatwo jest to realizowane przez ustawienie <xref:System.Windows.Forms.Control.Visible%2A> właściwości. Jeśli <xref:System.Windows.Forms.Control.Visible%2A> właściwość `true`, formant pojawi się w zwykły sposób. Jeśli `false`, kontrolki będą ukryte. Mimo że kod w kontroli nad może nadal działać podczas niewidoczne, nie można wchodzić w interakcje z kontrolką za pomocą interfejsu użytkownika. Jeśli chcesz utworzyć formant niewidoczne, który nadal odpowiada na dane wejściowe (na przykład kliknięć myszą) użytkownika, należy utworzyć formant przezroczysty. Aby uzyskać więcej informacji, zobacz [zapewniając ustawienie przezroczystego tła formantu](how-to-give-your-control-a-transparent-background.md).  
  
### <a name="to-make-your-control-invisible-at-run-time"></a>Aby ukrywanie formantu w czasie wykonywania  
  
1.  Ustaw <xref:System.Windows.Forms.Control.Visible%2A> właściwość `false`.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Windows.Forms.Control.Visible%2A>
- [Opracowywanie niestandardowych kontrolek formularzy Windows Forms za pomocą programu .NET Framework](developing-custom-windows-forms-controls.md)
- [Instrukcje: Zachować kontrolę z przezroczystym tłem](how-to-give-your-control-a-transparent-background.md)
