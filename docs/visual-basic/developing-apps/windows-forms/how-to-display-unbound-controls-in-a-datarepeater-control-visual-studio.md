---
title: 'Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: 698e518a4ed10ed6cf14ccafc6833b1acf8752db
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33588109"
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
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie powiązanych danych w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
