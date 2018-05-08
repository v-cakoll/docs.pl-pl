---
title: 'Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)'
ms.date: 07/20/2015
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
ms.openlocfilehash: b96fb33a0dcf80a86d1fcb6e219e5f35b1f7351c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)
Najczęściej używane <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania są wyświetlane powiązane dane z bazy danych lub inne źródła danych.  
  
 Oprócz formanty powiązane, można dodać inne formanty, takie jak statyczną etykietę lub obraz jest powtarzany na każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formantów niepowiązanych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Można także powiązać ze źródłem danych w czasie wykonywania przez ustawienie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` i przypisywanie źródło danych do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> właściwości. W takim przypadku należy zarządzać wszystkie interakcje ze źródłem danych. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Aby utworzyć DataRepeater powiązane z danymi  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  Przeciągnij uchwyt zmiany rozmiaru i pozycji do rozmiaru i pozycji formantu.  
  
     Należy pamiętać, że kontrolka ma dwóch regionach prostokątny. Górny obszar jest *szablon elementu*; formanty dodawane do szablonu zostanie powtórzona w każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania. Niższe region jest *okienka ekranu*, której elementy będą wyświetlane.  
  
     Można również rozmiaru i pozycji formant lub szablon elementu zmieniając **rozmiar** i **pozycji** właściwości w oknie właściwości.  
  
3.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niej. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
4.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla tabeli, która zawiera dane, które chcesz powiązać.  
  
5.  Zmień typ docelowej tabeli `Details` klikając `Details` na liście rozwijanej na węźle tabeli.  
  
6.  Wybierz węzeł tabeli i przeciągnij go na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     Można określić, jakie typy formantów są wyświetlane dla każdego pola. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Instrukcje: wyświetlanie niepowiązanych kontrolek w kontrolce DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Instrukcje: zmienianie wyglądu kontrolki DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z kontrolką DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
