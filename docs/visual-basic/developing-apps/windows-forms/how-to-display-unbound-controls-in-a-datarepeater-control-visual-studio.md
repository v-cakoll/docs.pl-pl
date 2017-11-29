---
title: "Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 3e96219f0ea8b8198967e9fa3c6e5afb824352db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)
Oprócz formanty powiązane, można dodać inne formanty <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, na przykład statyczną etykietę lub obraz jest powtarzany na każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
> [!NOTE]
>  Musi mieć co najmniej jeden formant związany <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> lub nie będą wyświetlane żadne w czasie wykonywania.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Aby dodać niepowiązanych formantów DataRepeater  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  Przeciągnij uchwyt zmiany rozmiaru i pozycji do rozmiaru i pozycji formantu.  
  
     Możesz również rozmiar i położenie kontrolki, zmieniając **rozmiar** i **pozycji** właściwości w oknie właściwości.  
  
3.  Dodaj co najmniej jeden formant powiązany z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie powiązanych danych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Przeciągnij formant z **przybornika** na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     Należy pamiętać, że kontrolka ma dwóch regionach prostokątny. Wewnętrzny region jest *szablon elementu*; formanty dodawane do szablonu zostanie powtórzona w każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania. Zewnętrzne region jest *okienka ekranu*, której elementy będą wyświetlane; formantów, które są dodawane do tego obszaru nie będą wyświetlane w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z formantem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Porady: wyświetlanie powiązanych danych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
