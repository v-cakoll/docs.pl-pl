---
title: 'Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, adding unbound controls
- DataRepeater
- displaying unbound data
ms.assetid: f234fa40-5a13-4209-930e-7c5f81e86e66
ms.openlocfilehash: a20e1ba83d1963bc3d4c135817767ee02fcbdeda
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54730792"
---
# <a name="how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio"></a>Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater (Visual Studio)
Oprócz formanty powiązania, warto dodać inne formanty do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>, na przykład etykieta statyczna lub obraz jest powtarzany w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
> [!NOTE]
>  Musisz również posiadać co najmniej jedną kontrolkę powiązanej <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> lub nic nie będą wyświetlane w czasie wykonywania.  
  
### <a name="to-add-unbound-controls-to-a-datarepeater"></a>Aby dodać niepowiązanej kontrolki DataRepeater  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  Przeciągając uchwyty zmiany rozmiaru i położenia rozmiar i położenie formantu.  
  
     Można także rozmiar i położenie formantu, zmieniając **rozmiar** i **pozycji** właściwości w oknie dialogowym właściwości.  
  
3.  Dodaj co najmniej jeden formant powiązany z danymi do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md).  
  
4.  Przeciągnij formant z **przybornika** na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
     Należy pamiętać, że kontrolka ma dwa regiony prostokątny. Wewnętrzny region jest *szablon elementu*; formantów dodanych do szablonu zostanie powtórzona w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania. Zewnętrzne region jest *okienka ekranu*, której elementy będą wyświetlane; formanty, które są dodawane do tego regionu nie będą wyświetlane w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
