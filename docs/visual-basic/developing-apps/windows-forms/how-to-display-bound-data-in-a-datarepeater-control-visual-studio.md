---
title: 'Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: dbcd814edb78c54ce5629a1a8761142674fe6135
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684622"
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Instrukcje: Wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)
Najbardziej powszechnym zastosowaniem programu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli jest wyświetlanie powiązanych danych z bazy danych lub innego źródła danych.  
  
 Oprócz formanty powiązania, warto dodać inne kontrolki, takie jak etykieta statyczna lub obraz jest powtarzany w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli. Aby uzyskać więcej informacji, zobacz [jak: Wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Możesz również powiązać ze źródłem danych w czasie wykonywania, ustawiając <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` i źródło danych w celu przypisywania <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> właściwości. W takim przypadku należy zarządzać wszystkie interakcje ze źródłem danych. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Aby utworzyć DataRepeater powiązanych z danymi  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> z kontrolować **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontener formantu.  
  
2.  Przeciągając uchwyty zmiany rozmiaru i położenia rozmiar i położenie formantu.  
  
     Należy pamiętać, że kontrolka ma dwa regiony prostokątny. Jest górnego regionu *szablon elementu*; formantów dodanych do szablonu zostanie powtórzona w każdym elemencie w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania. Jest dolnego regionu *okienka ekranu*, gdzie elementy zostaną wyświetlone.  
  
     Można także rozmiar i położenie szablonu elementu lub formantu, zmieniając **rozmiar** i **pozycji** właściwości w oknie dialogowym właściwości.  
  
3.  Na **danych** menu, kliknij przycisk **Pokaż źródła danych**.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niego. Aby uzyskać więcej informacji, zobacz [dodasz nowe źródła danych](/visualstudio/data-tools/add-new-data-sources).  
  
4.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla tabeli, która zawiera dane, które chcesz powiązać.  
  
5.  Zmień upuszczany typ tabeli, aby `Details` , klikając pozycję `Details` w węźle tabeli na liście rozwijanej.  
  
6.  Wybierz węzeł tabeli i przeciągnij go na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontroli.  
  
     Można określić, jakie typy kontrolek będą wyświetlane dla każdego pola. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Zobacz także
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [Instrukcje: Wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)
- [Instrukcje: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)
- [Instrukcje: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)
- [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
